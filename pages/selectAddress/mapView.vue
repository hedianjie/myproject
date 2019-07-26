<template>
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
		></map>
	</view>
</template>

<script>
	import config from '@/config.default.js';
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
				
				controls: [{
					id: 1,
					position: {
						left: 0,
						top: 0
					},
					iconPath: "../../static/logo.png"
				}]
			}
		},
		
		methods: {
			
			// 移动地图位置 获取地图中心点 并且获取中心点附近商家
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
						// 设置中心点
						_this.latitude = latitude;
						_this.longitude = longitude;
						_this.getNearby(longitude, latitude);
					}
				})
			},
			
			// 根据经纬度获取附近商家
			getNearby(longitude, latitude){
				const _this = this;
				const format = this.formatLongitudeLatitude(6, longitude, latitude);
				const ary = [];
				
				uni.request({
					url: "https://restapi.amap.com/v3/place/around",
					data: {
						key: config.amapKey,
						location: `${format.longitude},${format.latitude}`,
						city: this.cityCode,
						citylimit: true,
						radius: 200
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
						_this.submit(ary);
					}
				})
			},
			
			// 获取当前定位 经纬度 移动当前定位
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
				let times = 1;
				for (var i = 0 ;i < size; i++) {times = times * 10};
				
				console.log(times)
				return {
					longitude: Math.round(longitude * times) / times,
					latitude: Math.round(latitude * times) / times,
				}
			},
			
			/**
			 * @param {Object} data格式化后的搜索结果数据
			 */
			submit(data) {
				if(data) {
					this.$emit("around", data)
				}
			}
			
		},
		
		
		mounted() {
			window.setInterval(() =>{
				this.getCurrentLocation();
			}, 1000);
			
			// 初始化获取自身周围
			this.getNearby(this.longitude, this.latitude)
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
</style>
