<template>
	<view class="content">
		<search-address @selected="submit"></search-address>
		
		<map-view @around="regionChange"></map-view>
		<scroll-view scroll-y="true" class="list-wrapper">
			<view v-for="item in addressList" class="list">
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
	import searchAddress from "./searchAddress.vue";
	import mapView from "./mapView.vue"
	export default {
		data() {
			return {
				addressList: []
			}
		},
		methods: {
			regionChange(addressList) {
				this.addressList = addressList;
			}
		},
		components: {
			searchAddress,
			faIcon,
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
