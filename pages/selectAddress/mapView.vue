<template>
	<view>
		<view class="map-wrapper" :style="{height: mapHeight + 'px'}">
			<map 
				id="map"
				name="" 
				:longitude="longitude" 
				:latitude="latitude"
				:markers="markers"
				show-location
				@regionchange="regionChange"
				:controls="controls"
				scale="18"
			>
				<cover-view class="controls-view">
					<cover-image src="../../static/map59.png"></cover-image>
				</cover-view>
			</map>
		</view>
		<scroll-view scroll-y="true" class="list-wrapper" @scrolltolower="turnPage">
			<view v-for="item in addressList" class="list" @click="submit(item)">
				<view class="list-icon">
					<fa-icon type="map-marker" size="26" color="#333333"></fa-icon>
				</view>
				<view class="list-conetnt">
					<view class="list-header">{{item.name}}</view>
					<view class="list-tip">{{item.address}}</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	import config from '@/config.default.js';
	
	/**
	 * 根据经纬度获取附近商家
	 * @param {String} location经纬度字符串 (经度,纬度)
	 * @param {Number} city城市编码
	 * @param {String} serach搜索关键字
	 * @param {String} amapkey地图key
	 * @param {Number} page分页
	 */
	const getPOILocation = (location, city, search, amapkey, page) => {
		return new Promise((resolve,reject) => {
			const ary = [];
			uni.request({
				url: "https://restapi.amap.com/v3/place/around",
				data: {
					key: amapkey,
					citylimit: true,
					radius: 200,
					types: "010000|020000|030000|040000|050000|060000|070000|080000|090000|100000|110000|120000|130000|140000|150000",
					page,
					location,
					city,
					search
				},
				method: "GET",
				success(res) {
					res = res.data;
					if(res.status == 1) {
						for(var i = 0 ; i < res.pois.length; i++ ){
							const cur = res.pois[i];
			
							ary.push({
								name: cur.name,
								address: cur.address,
								location: {
									longitude: cur.location.split(',')[0],
									latitude: cur.location.split(',')[1]
								},
								distance: cur.distance,
								cityname: cur.cityname,
								cityCode: cur.cityCode,
							});
						}
					}
					else {
						uni.showToast({
							title: `获取周围信息失败: ${res.info}`
						})
					}
				},
				fail(res) {
					uni.showToast({
						title: `error: 获取周围信息失败: ${res}`
					});
				},
				complete() {
					resolve(ary);
				}
			})
		})
	}
	
	
	export default{
		props: {
			cityCode:{
				type: String,
				default: ""
			}
		},
		created() {
			const _this = this;
			const winInfo = uni.getSystemInfoSync();
			const mapHeight = winInfo.windowHeight - 56 - 250;
			
			this.mapHeight = mapHeight;
			this.mapContext = uni.createMapContext('map',this);
			// 将自身点设置成中心点
			// 假中心点
			this.longitude = 116.434371; // 精度
			this.latitude = 39.922344; // 维度
			// uni.getLocation({
			// 	type: 'gcj02',
			// 	success(res) {
			// 		_this.latitude = res.latitude;
			// 		_this.longitude = res.longitude;
			// 	},
			// })
			this.controls[0].position.left = winInfo.windowWidth / 2 - 36;
			this.controls[0].position.top = mapHeight / 2 - 36;
			
		},
		data() {
			return {
				longitude: 116.434371, // 精度
				latitude: 39.922344, // 维度
				markers: [
					{
						longitude: 116.434371, // 精度
						latitude: 39.922344, // 维度
					}
				],
				
				// controls:[{//在地图上显示控件，控件不随着地图移动
				// 	id:1,//控件id
				// 	iconPath:'../../static/map59.png',//显示的图标	
				// 	position:{//控件在地图的位置
				// 		left:150,
				// 		top:150,
				// 		width:10,
				// 		height:10
				// 	},	
				// }],
				
				addressList: [],
				scrollTop: 0,
				page: 1,
				pageFlag: true, // 是否可以继续分页
				
			}
		},
		
		methods: {
			
			/**
			 * 移动地图位置 获取地图中心点 并且获取中心点附近商家
			 */
			regionChange(){
				
				const _this = this;
				let latitude, longitude;
				
				this.mapContext.getCenterLocation({
					success(res) {
						console.log(res)
						longitude = res.longitude;
						latitude = res.latitude;
					},
					fail(res) {
						console.log(res, '获取<当前中心点位置>出错，暂时用假数据代替');
						longitude = 116.434371; // 精度
						latitude = 39.922344; // 维度
					},
					complete() {
						if(_this.latitude == latitude && _this.longitude == longitude) {
							return console.log('地图位置没有移动！');
						}
						
						_this.latitude = latitude;				// 设置中心点
						_this.longitude = longitude;			// 设置中心点
						_this.addressList = [];					// 初始化地址列表
						_this.scrollTop = 0;					// 设置滚动条在最上
						_this.page = 1;							// 设置为第一页
						_this.pageFlag = true;					// 设置可继续分页状态
						_this.getNearby(longitude, latitude); 	// 获取当前位置搜索poi
						
					}
				})
			},
			
			/**
			 * 根据经纬度获取附近商家
			 * @param {Object} longitude经度
			 * @param {Object} latitude纬度
			 */
			async getNearby(longitude, latitude){
				const format = this.formatLongitudeLatitude(6, longitude, latitude);
				const ary = await getPOILocation(
					`${format.longitude},${format.latitude}`,
					this.cityCode,
					'',
					config.amapKey,
					this.page
				)
				.then(list => list);
				
				if(ary.length) {
					for(let i = 0 ; i < ary.length; i++) {
						this.addressList.push(ary[i])
					}
				}
				else{
					this.pageFlag = false; // 如果已经没有结果 禁止继续翻页
				}
			},
			
			/**
			 * 获取当前定位 经纬度 移动当前定位
			 */
			getCurrentLocation() {
				const _this = this;
				let latitude, longitude;
				
				uni.getLocation({
					type: 'gcj02',
					success(res) {
						latitude = res.latitude;
						longitude = res.longitude;
					},
					fail(res) {
						// console.log(res, '获取<当前位置>出错，暂时用假数据代替');
						longitude = 116.434371; // 精度
						latitude = 39.922344; // 维度
						
					},
					complete() {
						if(_this.markers[0].latitude == latitude && _this.markers[0].longitude == longitude) {
							// return console.log('用户没有移动！');
							return;
						}
						
						_this.markers = [{
							longitude: longitude, // 精度
							latitude: latitude, // 维度
						}]
					}
				})
			},
			
			/**
			 * 格式化经纬度 截取到小数点多少位
			 * @param {Object} size格式化长度
			 * @param {Object} longitude经度
			 * @param {Object} latitude纬度
			 */
			formatLongitudeLatitude(size, longitude, latitude) {
				let times = 1, i;
				for (i = 0; i < size; i++) {times = times * 10};
				return {
					longitude: Math.round(longitude * times) / times,
					latitude: Math.round(latitude * times) / times,
				}
			},
			
			/**
			 * 翻页
			 */
			turnPage() {
				if(this.pageFlag) {
					this.page++;
					this.getNearby(this.longitude, this.latitude);
				}
			},
			
			/**
			 * @param {Object} 点击对象
			 */
			submit(data) {
				if(data) {
					this.$emit("submit", data);
				}
			}
		},
		
		
		mounted() {
			window.setInterval(() =>{
				this.getCurrentLocation();
			}, 1000);
			
			// 初始化获取自身周围
			this.getNearby(this.longitude, this.latitude)
		},
		
		components:{
			faIcon
		}
	}
</script>

<style scoped>
	.map-wrapper{
		width: 100%;
	}
	.map-wrapper map{
		width: 100%;
		height: 100%;
	}
	.controls-view{
		width: 30px;
		height: 40px;
		position: absolute;
		left: 50%;
		margin-left: -15px;
		top: 50%;
		margin-top: -40px;
	}
	.list-wrapper{
		height: 250px;
		border-top: 1px solid #eee;
		box-shadow: 0 0 10px #ccc;
		background: #ffffff;
	}
	.list-wrapper .list{
		padding: 10px 10px;
		padding-left: 50px;
		position: relative;
		/* display: flex;
		align-items: center;
		justify-content: space-between;
		border-bottom: 1px solid #eee; */
	}
	.list-wrapper .list .list-icon{
		position: absolute;
		top: 10px;
		left: 10px;
		height: 45px;
		line-height: 45px;
		width: 30px;
		text-align: center;
	}
	.list-wrapper .list .list-header{
		font-size: 16px;
		font-weight: bold;
		color: #333333;
		overflow: hidden;
		word-break: break-all;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
	.list-wrapper .list .list-tip{
		font-size: 14px;
		color: #999999;
		margin-top: 5px;
		overflow: hidden;
		word-break: break-all;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
	.list-wrapper .list.active .list-header{
		color: #007AFF;
	}
	.list-wrapper .list.active .list-icon{
		color: #007AFF !important;
	}
</style>
