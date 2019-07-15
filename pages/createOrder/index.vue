<template>
	<view class="content">
		<view class="layout-header">
			<!-- 地址 -->
			<view class="address-wrapper">
				<view class="m-b-10">
					<text class="address-tag">公司</text>
					<text class="address-text">中医火鸡士大夫奥德赛as电费02中医火鸡士大夫奥德赛as电费02</text>
				</view>
				<view>
					<text class="address-name">何(先生)</text>
					<text class="address-phone">15567702010</text>
				</view>
				<view class="address-icon"><fa-icon type="angle-right" size="20" color="#777777"></fa-icon></view>
			</view>
			<!-- 选择时间 -->
			<view class="time-wrapper">
				<view class="time-text">立即到达</view>
				<view class="time-content">大约22:49到达</view>
				<view class="time-icon"><fa-icon type="angle-right" size="20" color="#777777"></fa-icon></view>
			</view>
		</view>
		<view class="layout-content"></view>
		<view class="layout-footer"></view>
	</view>
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		components: {faIcon}
	}
</script>

<style scoped>
	page{
		background: #F8F9FA;
	}
	.content{
		background: linear-gradient(top, #007AFF, #ffffff, #ffffff);
	}
	.m-b-20{
		margin-bottom: 20px;
	}
	.m-b-15{
		margin-bottom: 15px;
	}
	.m-b-10{
		margin-bottom: 10px;
	}
	.layout-header{
		margin: 10px;
		margin-bottom: 5px;
		margin-top: 0;
		background: #ffffff;
		box-shadow: 0 0 12px #cccccc;
		border-radius: 6px;
	}
	.address-wrapper{
		position: relative;
		padding: 25px 12px;
		padding-right: 30px;
		padding-bottom: 20px;
	}
	
	.address-wrapper .address-tag {
		display: inline-block;
		background: #28A745;
		color: #ffffff;
		padding: 2px 4px;
		font-size: 12px;
		margin-right: 5px;
		transform: scale(0.9);
	}
	.address-wrapper .address-text {
		font-size: 17px;
		font-weight: bold;
		line-height: 24px;
		color: #333;
	}
	.address-wrapper .address-name,
	.address-wrapper .address-phone{
		font-size: 13px;
		color: #333;
		margin-right: 20px;
	}
	.address-wrapper .address-icon{
		position: absolute;
		top: 50%;
		right: 10px;
		margin-top: -10px;
	}
	.time-wrapper{
		position: relative;
		padding: 20px 12px;
		padding-right: 30px;
		border-top: 1px solid #ccc;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.time-wrapper .time-text{
		font-size: 15px;
		color: #333;
		font-weight: bold;
	}
	.time-wrapper .time-content{
		color: #007AFF;
		font-size: 16px;
		font-weight: bold;
	}
	.time-wrapper .time-icon{
		position: absolute;
		top: 50%;
		right: 10px;
		margin-top: -10px;
	}
</style>
