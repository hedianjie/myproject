<template>
	<view class="content">
		<view class="layout-header">
			<!-- 地址 -->
			<view class="address-wrapper wrapper bar">
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
			<my-picker @arriveTime="getArriveTime">
				<view class="time-wrapper wrapper" slot="picker">
					<view v-if="true" class="time-text">约定时间</view>
					<view v-else class="time-text">立即到达</view>
					<view class="time-content">大约22:49到达</view>
					<view class="time-icon"><fa-icon type="angle-right" size="20" color="#777777"></fa-icon></view>
				</view>
			</my-picker>
		</view>
		<view class="layout-content wrapper">
			<view class="info-title">订单详细</view>
			<view class="info-list">
				<view class="info-list-left">应付款</view>
				<view class="info-list-right">￥12.9元</view>
			</view>
			<view class="info-list">
				<view class="info-list-left">追加红包</view>
				<view class="info-list-right">￥5</view>
			</view>
			<view class="info-list">
				<view class="info-list-left">优惠券</view>
				<view class="info-list-right color-red">-￥5</view>
			</view>
			
			<view class="info-list total-info bar-top">
				<view class="info-list-left f-s-18 f-w-b">总计</view>
				<view class="info-list-right f-s-20">￥5</view>
			</view>
		</view>
		<view class="layout-footer"></view>
	</view>
</template>

<script>
	import myPicker from "./picker.vue";
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			// 选择到达时间
			getArriveTime(data) {
				console.log(data);
			}
		},
		components: {
			faIcon,
			myPicker
		}
	}
</script>

<style scoped>
	page{
		background: #F8F9FA;
	}
	.content{
		background: linear-gradient(top, #007AFF, #ffffff, #ffffff);
	}
	.bar{
		border-bottom: 1px solid #ccc;
	}
	.bar-top{
		border-top: 1px solid #ccc;
	}
	.wrapper{
		padding: 25px 12px;
	}
	.layout-header,
	.layout-content{
		margin: 10px;
		margin-bottom: 7px;
		margin-top: 0;
		background: #ffffff;
		box-shadow: 0 0 12px #cccccc;
		border-radius: 6px;
	}
	
	/**
	 * layout-header
	 */
	.address-wrapper{
		position: relative;
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
		padding: 17px 12px;
		padding-right: 30px;
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
	
	/**
	 * layout-content
	 */
	.info-title{
		font-size: 16px;
		font-weight: bold;
		color: #333;
		margin-bottom: 15px;
	}
	
	.info-list{
		padding: 15px 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		position: relative;
	}
	.info-list .info-list-left{
		font-size: 14px;
	}
	.info-list .info-list-right{
		font-size: 15px;
		font-weight: bold;
		
	}
</style>
