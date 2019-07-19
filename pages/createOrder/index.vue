<template>
	<view class="content">
		<view class="layout-header">
			<!-- 地址 -->
			<navigator class="address-wrapper wrapper bar" url="../addressList/index">
				<view class="m-b-10">
					<text class="address-tag">公司</text>
					<text class="address-text">中医火鸡士大夫奥德赛as电费02中医火鸡士大夫奥德赛as电费02</text>
				</view>
				<view>
					<text class="address-name">何(先生)</text>
					<text class="address-phone">15567702010</text>
				</view>
				<view class="wrapper-icon"><fa-icon type="angle-right" size="20" color="#999999"></fa-icon></view>
			</navigator>
			<!-- 选择时间 -->
			<my-picker @arriveTime="getArriveTime">
				<view class="time-wrapper wrapper bar" slot="picker">
					<view v-if="true" class="wrapper-text">约定时间</view>
					<view v-else class="wrapper-text">立即到达</view>
					<view class="wrapper-content">大约22:49到达</view>
					<view class="wrapper-icon"><fa-icon type="angle-right" size="20" color="#999999"></fa-icon></view>
				</view>
			</my-picker>
			
			<!-- 支付方式 -->
			<my-picker-pay>
				<view class="pay-wrapper wrapper" slot="pickerView">
					<view class="wrapper-text">支付方式</view>
					<view class="wrapper-content"><fa-icon type="weixin" size="18" color="#42b983" margin="0 5px 0 0"></fa-icon>微信支付</view>
					<view class="wrapper-icon"><fa-icon type="angle-right" size="20" color="#999999"></fa-icon></view>
				</view>
			</my-picker-pay>
		</view>
		<view class="layout-content wrapper">
			<view class="info-title bar">订单详细</view>
			<view class="info-list list">
				<view class="list-left">应付款</view>
				<view class="list-right">￥12.9元</view>
			</view>
			<view class="info-list list">
				<view class="list-left">追加红包</view>
				<view class="list-right">￥5</view>
			</view>
			<view class="info-list list">
				<view class="list-left">优惠券</view>
				<view class="list-right color-red">-￥5</view>
				<view class="list-icon"><fa-icon type="angle-right" size="20" color="#999999"></fa-icon></view>
			</view>
			
			<view class="info-list list total-info bar-top">
				<view class="list-left f-s-16 f-w-b">总计</view>
				<view class="list-right f-s-18"><view class="total-info-tip">￥12.9</view>￥17.9元</view>
			</view>
			
		</view>
		<view class="layout-footer wrapper">
			<navigator class="remark-info list" url="../remarkInfo/index">
				<view class="list-left">订单备注</view>
				<view class="list-right">阿斯顿发送到发到付飒飒大法师打发阿斯顿发送到发到付飒飒大法师打发阿斯顿发送到发到付飒飒大法师打发</view>
				<view class="list-icon"><fa-icon type="angle-right" size="20" color="#999999"></fa-icon></view>
			</navigator>
		</view>
		
		<view class="position-submit">
			<view class="position-submit-left">
				<view class="price">￥23</view>
				<view class="vertical-line"></view>
				<view class="pric-tip">已优惠￥19</view>
			</view>
			<view class="position-submit-right">确认支付</view>
		</view>
	</view>
</template>

<script>
	import myPicker from "./picker.vue";
	import myPickerPay from "./pickerPay.vue";
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
			myPicker,
			myPickerPay
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
		border-bottom: 1px solid #dddddd;
	}
	.bar-top{
		border-top: 1px solid #dddddd;
	}
	.wrapper{
		padding: 25px 12px;
	}
	.wrapper .wrapper-text{
		font-size: 15px;
		color: #333;
		font-weight: bold;
	}
	.wrapper .wrapper-icon{
		position: absolute;
		top: 50%;
		right: 10px;
		margin-top: -10px;
	}
	.wrapper .wrapper-content{
		color: #333;
		font-size: 16px;
		font-weight: bold;
	}
	.layout-header,
	.layout-content,
	.layout-footer{
		margin: 10px;
		margin-bottom: 7px;
		margin-top: 0;
		background: #ffffff;
		box-shadow: 0 0 12px #cccccc;
		border-radius: 6px;
	}
	.layout-header .wrapper{
		position: relative;
		padding: 17px 12px;
		padding-right: 30px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.layout-content{
		padding: 15px 12px;
	}
	.list{
		padding: 15px 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		position: relative;
	}
	.list-left{
		font-size: 14px;
		white-space: nowrap;
	}
	.list-right{
		margin-right: 13px;
		font-size: 15px;
		font-weight: bold;
		white-space: nowrap;
		max-width: 70%;
		overflow: hidden;
		text-overflow: ellipsis;
		text-align: right;
	}
	.list-icon{
		position: absolute;
		top: 50%;
		right: 0;
		margin-top: -10px;
	}
	
	
	/**
	 * layout-header
	 */
	.address-wrapper{
		display: block !important;
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
/* 	.time-wrapper{
		position: relative;
		padding: 17px 12px;
		padding-right: 30px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	} */
/* 	.time-wrapper .time-text{
		font-size: 15px;
		color: #333;
		font-weight: bold;
	} */
	.time-wrapper .wrapper-content{
		color: #007AFF;
	}
/* 	.time-wrapper .time-icon{
		position: absolute;
		top: 50%;
		right: 10px;
		margin-top: -10px;
	} */
	/* .pay-wrapper{
		position: relative;
		padding-top: 17px;
		padding-bottom: 17px;
		padding-right: 30px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	} */
/* 	.pay-info-right{
		margin-right: 0;
	} */
	
	/* .pay-wrapper .pay-info-icon{
		position: absolute;
		top: 50%;
		right: 10px;
		margin-top: -10px;
	} */
	/**
	 * layout-content
	 */
	.info-title{
		font-size: 16px;
		font-weight: bold;
		color: #333;
		margin-bottom: 15px;
		padding-bottom: 15px;
	}
	.info-list.total-info{
		padding-bottom: 0;
	}
	.total-info-tip{
		font-size: 13px;
		font-weight: 400;
		text-decoration: line-through;
		color: #999999;
		display: inline-block;
		margin-right: 5px;
		vertical-align: bottom;
	}
	
	/**
	 * layout-footer
	 */
	.layout-footer{
		padding-top: 0;
		padding-bottom: 0;
	}
	.remark-info .list-right{
		font-weight: 400;
		font-size: 14px;
	}
	
	/**
	 * position-submit
	 */
	.position-submit{
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		background: #333333;
		height: 54px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.position-submit-left{
		display: flex;
		align-items: center;
		line-height: 54px;
		padding-left: 12px;
	}
	.position-submit-left .price{
		font-size: 20px;
		color: #fcfcfc;
	}
	.position-submit-left .vertical-line{
		width: 1px;
		height: 16px;
		background: #999999;
		margin: 0 10px;
	}
	.position-submit-left .pric-tip{
		color: #999999;
		font-size: 12px;
	}
	.position-submit-right{
		background: #77C646;
		color: #ffffff;
		padding: 0 16px;
		line-height: 54px;
		font-size: 20px;
	}
</style>
