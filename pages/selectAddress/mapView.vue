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
		></map>
	</view>
</template>

<script>
	export default{ 
		created() {
			const _this = this;
			const winInfo = uni.getSystemInfoSync();
			this.mapHeight = winInfo.windowHeight - 56 - 250;
			
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
		},
		data() {
			return {
				// mapHeight: 0,
				
				
				longitude: 116.434371, // 精度
				latitude: 39.922344, // 维度
				markers: [
					{
						longitude: 116.434371, // 精度
						latitude: 39.922344, // 维度
					}
				],
				// polyline: [{
				// 	points: [{"longitude":"116.434371","latitude":"39.922344"},{"longitude":"116.434366","latitude":"39.921992"},{"longitude":"116.434366","latitude":"39.921992"},{"longitude":"116.434379","latitude":"39.921563"},{"longitude":"116.434379","latitude":"39.921563"},{"longitude":"116.434379","latitude":"39.921519"},{"longitude":"116.434379","latitude":"39.921519"},{"longitude":"116.434401","latitude":"39.921094"},{"longitude":"116.434401","latitude":"39.921094"},{"longitude":"116.434414","latitude":"39.920677"},{"longitude":"116.434414","latitude":"39.920677"},{"longitude":"116.434431","latitude":"39.920304"},{"longitude":"116.434431","latitude":"39.920304"},{"longitude":"116.434444","latitude":"39.920052"},{"longitude":"116.434444","latitude":"39.920052"},{"longitude":"116.43447","latitude":"39.91954"},{"longitude":"116.43447","latitude":"39.91954"},{"longitude":"116.434475","latitude":"39.919453"},{"longitude":"116.434475","latitude":"39.919453"},{"longitude":"116.434505","latitude":"39.918633"},{"longitude":"116.434505","latitude":"39.918633"},{"longitude":"116.434523","latitude":"39.918451"},{"longitude":"116.434523","latitude":"39.918451"},{"longitude":"116.434536","latitude":"39.917982"},{"longitude":"116.434536","latitude":"39.917982"},{"longitude":"116.434562","latitude":"39.917244"},{"longitude":"116.434562","latitude":"39.917244"},{"longitude":"116.434601","latitude":"39.916497"},{"longitude":"116.434601","latitude":"39.916497"},{"longitude":"116.434622","latitude":"39.916063"},{"longitude":"116.434622","latitude":"39.916063"},{"longitude":"116.434631","latitude":"39.915764"},{"longitude":"116.434631","latitude":"39.915764"},{"longitude":"116.434635","latitude":"39.915703"}],
				// 	color: "#007AFF",
				// 	width: 5,
				// }]
				// polyline: 
			}
		},
		
		methods: {
			regionChange(){
				
				const _this = this;
				this.mapContext.getCenterLocation({
					success(res) {
						console.log(res)
						_this.latitude = res.latitude;
						_this.longitude = res.longitude;
						_this.markers[0].latitude = res.latitude;
						_this.markers[0].longitude = res.longitude;
					
						// _this.mapContext.setCenter( center );
						_this.mapContext.moveToLocation();
					}
				})
			}
		},
		mounted() {
			
			// this.appMap = this.mapContext.$getAppMap();
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
