<template>
	<view class="content">
		<view class="nav-tabs">
			<view class="nav-item active">全部订单</view>
			<view class="nav-item">待付款</view>
			<view class="nav-item">待评价</view>
			<view class="nav-item">退款</view>
		</view>
		
		<view class="nav-content">
			<!-- 全部订单 -->
			<view class="nav-list">
				<swipe-action :options="swipeActionOptions">
					<view class="field-column">
						<view class="column-header">
							<view class="column-header-sideleft"><fa-icon type="check-circle" size="16" margin="0 5px 0 0"></fa-icon>订单成功</view>
							<view class="column-header-sideright">￥14.2元</view>
						</view>
						<view class="column-content">
							地址：<text class="column-content-text">吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克</text>
						</view>
						<view class="column-footer">
							<view class="column-footer-sideleft"><fa-icon type="clock-o" size="14" margin="0 5px 0 0"></fa-icon>2019-11-11 23:11</view>
							<view class="column-footer-sideright"><button type="warn" size="mini">评价</button></view>
						</view>
					</view>
				</swipe-action>
				<swipe-action :options="swipeActionOptions">
					<view class="field-column">
						<view class="column-header">
							<view class="column-header-sideleft"><fa-icon type="check-circle" size="16" margin="0 5px 0 0"></fa-icon>订单成功</view>
							<view class="column-header-sideright">￥14.2元</view>
						</view>
						<view class="column-content">
							地址：<text class="column-content-text">吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克</text>
						</view>
						<view class="column-footer">
							<view class="column-footer-sideleft"><fa-icon type="clock-o" size="14" margin="0 5px 0 0"></fa-icon>2019-11-11 23:11</view>
							<view class="column-footer-sideright"><button type="warn" size="mini">评价</button></view>
						</view>
					</view>
				</swipe-action>
				<swipe-action :options="swipeActionOptions">
					<view class="field-column">
						<view class="column-header">
							<view class="column-header-sideleft"><fa-icon type="check-circle" size="16" margin="0 5px 0 0"></fa-icon>订单成功</view>
							<view class="column-header-sideright">￥14.2元</view>
						</view>
						<view class="column-content">
							地址：<text class="column-content-text">吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克吉林大路放假阿里山大街飞拉萨的解放路口撒娇的弗兰克</text>
						</view>
						<view class="column-footer">
							<view class="column-footer-sideleft"><fa-icon type="clock-o" size="14" margin="0 5px 0 0"></fa-icon>2019-11-11 23:11</view>
							<view class="column-footer-sideright">
								<button type="default" size="mini">取消订单</button>
								<button type="warn" size="mini">评价</button>
							</view>
						</view>
					</view>
				</swipe-action>
			</view>
		</view>
	</view>
	
	
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	import swipeAction from "@/components/uni-swipe-action/uni-swipe-action.vue";
	
	export default {
		data() {
			return {
				swipeActionOptions: [{
					text: '删除',
					style: {
						backgroundColor: '#dd524d'
					}
				}]
			}
		},
		methods: {
			
		},
		components: {
			faIcon,
			swipeAction
		}
	}
</script>

<style scoped>
	page{
		background: #F8F9FA;
	}
	.content{
		padding-top: 44px;
	}
	.nav-tabs{
		position: fixed;
		top: 44px;
		left: 0;
		width: 100%;
		display: flex;
		background: #DDDDDD;
		color: #999;
		padding: 12px 0;
		font-size: 15px;
		justify-content: space-around;
		align-items: center;
	}
	.nav-tabs .nav-item.active{
		color: #333;
		font-weight: bold;
		position: relative;
	}
	.nav-tabs .nav-item.active:after{
		position: absolute;
		bottom: -4px;
		left: 50%;
		content: "";
		width: 24px;
		margin-left: -12px;
		height: 2px;
		border-radius: 2px;
		background: #007AFF;
	}
	
	.nav-content{
		background: #ffffff;
	}
	
	.field-column{
		padding: 10px 20px;
		border-bottom:  1px solid #ddd;
	}
	.column-header{
		background: #F8F9FA;
		border: 4px 4px;
		padding-bottom: 10px;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-weight: bold;
	}
	.column-header-sideleft{
		font-size: 16px;
	}
	.column-header-sideright{
		font-size: 14px;
	}
	
	.column-content{
		font-size: 16px;
		color: #007AFF;
		overflow: hidden;
		text-overflow: ellipsis;
		/*设置成弹性盒子 */
		display: -webkit-box;
		/*显示的个数 */
		-webkit-line-clamp: 2;
		/* 属性规定框的子元素应该被水平或垂直排列。 */
		-webkit-box-orient: vertical;
	}
	.column-content-text{
		color: #333333;
		text-indent: 2px;
	}
	
	.column-footer{
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding-top: 10px;
	}
	.column-footer-sideleft{
		font-size: 14px;
		color: #333;
	}
</style>
