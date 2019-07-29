<template>
	<view class="content">
		<search-address @selected="submit"></search-address>
		
		<map-view @submit="submit"></map-view>
		
	</view>
</template>

<script>
	
	import searchAddress from "./searchAddress.vue";
	import mapView from "./mapView.vue"
	export default {
		data() {
			return {
				// addressList: []
			}
		},
		methods: {
			submit(data) {
				console.log(data);
			}
			// regionChange(addressList) {
			// 	this.addressList = addressList;
			// }
		},
		components: {
			searchAddress,
			mapView
		}
	}
</script>

<style>
	page{
		background: #F8F9FA;
	}
	page-body{
		height: 100%;
	}
	.content{
		padding-top: 56px;
		height: 100%;
	}
	
</style>
