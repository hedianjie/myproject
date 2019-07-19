<template>
	<view class="content">
		
		<!-- 头部 -->
		<uni-nav-bar statusBar="true" shadow="true">
			<view class="navigation-left" slot="left" @click="switchArea">
				<fa-icon type="map-marker" size="20" margin="0 5px 0 0"></fa-icon>{{position_name}}
			</view>
			<view class="navigation-right" slot="right">
				<fa-icon type="commenting" :margin="'0 '+ messageMargin +'px 0 0'" size="22" @click="messageNotification"></fa-icon>
				<view v-if="messageLength && messageLength >= 1" class="message-badge">
					<uni-badge :text="messageLength >= 100 ? '99+' : messageLength" type="error" size="small"></uni-badge>
				</view>
			</view>
		</uni-nav-bar>
		
		<!-- 内容 -->
		 <view class="wrapper">
			 
			 <!-- 选项卡 -->
			<view class="box-title">选择垃圾种类</view>
			<view class="nav-tabs">
				<view class="nav-item" :class="tab == 0 ? 'active' : ''" @click="tab = 0">
					<view class="nav-item-text">少量</view>
					<view class="water-wrapper water-30">
						<view class="water water-first"></view>
						<view class="water water-second"></view>
						<view class="water water-third"></view>
					</view>
				</view>
				<view class="nav-item" :class="tab == 1 ? 'active' : ''" @click="tab = 1">
					<view class="nav-item-text">普通</view>
					<view class="water-wrapper water-50">
						<view class="water water-first"></view>
						<view class="water water-second"></view>
						<view class="water water-third"></view>
					</view>
				</view>
				<view class="nav-item" :class="tab == 2 ? 'active' : ''" @click="tab = 2">
					<view class="nav-item-text">多量</view>
					<view class="water-wrapper water-80">
						<view class="water water-first"></view>
						<view class="water water-second"></view>
						<view class="water water-third"></view>
					</view>
				</view>
			</view>
			
			<!-- 选项内容 -->
			<view class="nav-content">
				<view v-show="tab == 0" class="nav-list">{{pricing.xs}}<span class="font-sm">元</span></view>
				<view v-show="tab == 1" class="nav-list">{{pricing.sm}}<span class="font-sm">元</span></view>
				<view v-show="tab == 2" class="nav-list">{{pricing.lg}}<span class="font-sm">元</span></view>
			</view>
			<button type="warn" @click="submit" :disabled="btn_disabled" :loading="btn_loading">确认发起订单</button>
			
			<!-- 友情提示 -->
			<view class="content-tip">
				<view>
					<fa-icon type="exclamation-circle" size="18" color="#999999" margin="0 5px 0 0"></fa-icon>友情提醒
				</view>
				<view>
					金额会根据省份地区的不同有所浮动！
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	
	export default {
		data() {
			return {
				/**
				 * 头部信息
				 */ 
				position_name: "东安开运福里B10", // 地理名称
				messageLength: 0, // 消息条数
				
				/**
				 * 内容信息
				 */
				tab: 1, // 选项卡被选中
				pricing: {
					xs: 11.9, // 少量
					sm: 12.9, // 普通
					lg: 15.9, // 多量
				},
				btn_loading: false, // 按钮状态
				btn_disabled: false
			}
		},
		computed: {
			messageMargin() {
				if (this.messageLength >= 10) {
					return 15;
				}
				else if (this.messageLength >= 100) {
					return 20;
				}
				else if (this.messageLength < 1) {
					return 0;
				}
				else {
					return 10;
				}
			}
		},
		methods: {
			// 切换地区
			switchArea() {
				console.log("click,left")
			},
			// 消息通知
			messageNotification() {
				console.log("message")
			},
			
			submit() {
				console.log(1);
				this.btn_loading = true;
				this.btn_disabled = true;
				uni.navigateTo({
					url: "../createOrder/index",
				});
			}
		},
		components: {
			faIcon,
		}
	}
</script>

<style scoped>
	page{
		background: #F8F9FA;
	}
	.content{
		/* background: #F8F9FA; */
		/* height: 100%; */
	}
	.font-sm{
		font-size: 22px;
	}
	.content-tip{
		margin-top: 30px;
		font-size: 14px;
		color: #999999;
		text-align: center;
		line-height: 24px;
	}
	.wrapper {
		padding: 0 22px;
	}
	.navigation-left{
		font-size: 18px;
		font-weight: 500;
	}
	.message-badge{
		position: absolute;
		top: 10px;
		right: 0;
		line-height: 0;;
	}
	.wrapper{
		margin-top: 30px;
	}
	.box-title{
		line-height: 32px;
		font-size: 17px;
		font-weight: 500;
		margin-bottom: 20px;
	}
	.nav-tabs{
		display: flex;
		align-items: center;
		flex-direction: row;
		justify-content: space-between;
	}
	.nav-tabs .nav-item{
		width: 200upx;
		height: 200upx;
		line-height: 200upx;
		text-align: center;
		border-radius: 50%;
		border: 1px solid #ccc;
		transform: scale(.85);
		opacity: .65;
		overflow: hidden;
		transition: all .2s ease-in-out;
	}
	.nav-tabs .nav-item.active{
		transform: scale(1.1);
		opacity: 1;
	}
	
	.nav-tabs .nav-item .nav-item-text{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 1;
	}
	
	.nav-list{
		position: relative;
		text-align: center;
		margin-top: 20px;
		margin-bottom: 20px;
		font-size:  38px;
		font-weight: bold;
		color: #007AFF;
		padding : 20px 0;
		background: #fff;
		border-radius: 5px;
		box-shadow: 0 0 14px #F1F1F1;
	}
/* 	.nav-list:before{
		position: absolute;
		top: -20px;
		left: 10px;
		content: "";
		width: 0;
		height: 0;
		border-width: 10px;
		border-color: transparent transparent #fff transparent;
		border-style: solid;
		
	} */
	
	/** 波纹动画 **/
	@-webkit-keyframes move_wave {
		0% { background-position:0 0 }
		to { background-position:532px 0 }
	}

	@keyframes move_wave {
		0% { background-position:0 0 }
		to { background-position:532px 0 }
	}
	.water-wrapper{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	.water{
		height: 100%;
		background: url(../../static/water.png) repeat-x;
		position: absolute;
		width: 100%;
		-webkit-animation: move_wave 4s linear infinite;
		animation: move_wave 4s linear infinite;
	}
	.water-first{
		opacity: .5;
		background-position: 0 0;
		-webkit-animation: move_wave 10s linear infinite;
		animation: move_wave 10s linear infinite;
	}
	.water-second{
		opacity: .5;
		background-position: 120px 0;
		-webkit-animation: move_wave 10s linear infinite;
		animation: move_wave 10s linear infinite;
	}
	.water-third{
		opacity: .3;
		background-position: 60px 0;
		-webkit-animation: move_wave 8s linear infinite;
		animation: move_wave 8s linear infinite;
	}
	
	.water-100 {
		top: 0
	}
	.water-90 {
		top: 10%
	}
	.water-80 {
		top: 20%
	}
	.water-70 {
		top: 30%
	}
	.water-60 {
		top: 40%
	}
	.water-50 {
		top: 50%
	}
	.water-40 {
		top: 60%
	}
	.water-30 {
		top: 70%
	}
	.water-20 {
		top: 80%
	}
	.water-10 {
		top: 90%
	}
	.water-0 {
		top: 100%
	}
</style>
