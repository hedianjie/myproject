<template>
	<view>
		<div :class="mask_class" :style="mask_style" @click="hide"></div>
		<div :class="picker_class">
			<div class="h-uni-picker-header">
				选择支付方式
				<div class="h-uni-picker-close" @click="hide"><fa-icon type="times" size="20" color="#333"></fa-icon></div>
				<!-- <div class="h-uni-picker-action h-uni-picker-action-cancel" @click="hide">取消</div>
				<div class="h-uni-picker-action h-uni-picker-action-confirm" @click="submit(value)">确定</div> -->
			</div>
			<uni-picker-view class="h-uni-picker-content">
				<view class="h-uni-picker-list" v-for="(item, index) in pay_list" @click="change(item.key)">
					<view class="h-uni-picker-list-left">
						<fa-icon :type="item.icon" size="16" margin="0 5px 0 0" :color="item.color"></fa-icon>{{item.name}}
					</view>
					<view class="h-uni-picker-list-right">
						<fa-icon type="check-circle" size="20" margin="0 5px 0 0" :color="value == item.key ? '#42b983' : ''"></fa-icon>
					</view>
				</view>
			</uni-picker-view>
		</div>
		<view @click="show">
			<slot name="pickerView"></slot>
		</view>
	</view>
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	export default {
		props: {
			defaultValue: {
				type: Number,
				default() {
					return 0;
				}
			}
		},
		data() {
			return {
				is: false,
				mask_class: "h-uni-mask",
				mask_style: "display: none;",
				picker_class: "h-uni-picker",
				pay_list: [
					{
						key: 0,
						name: "微信",
						icon: "weixin",
						color: "#42b983"
					},
					{
						key: 1,
						name: "支付宝",
						icon: "",
						color: ""
					}
				],
				value: 0
			}
		},
		
		methods: {
			submit(key) {
				if(index === null || index === undefined || index > this.pay_list.length || index < 0) {
					uni.showModal({
						title: "系统提示",
						content: "选中内容有误，请重新选择！",
						showCancel: false,
					});
					return;
				}
				
				this.$emit("change", key);
				this.hide();
			},
			
			show() {
				this.is = true;
				this.mask_style = ""
				this.mask_class = "h-uni-mask h-uni-fade-enter-active",
				this.picker_class = "h-uni-picker h-uni-picker-toggle",
				setTimeout(() =>{
					this.mask_class = "h-uni-mask";
					
				}, 250);
			},
			
			hide() {
				this.is = false;
				this.mask_class = "h-uni-mask h-uni-fade-leave-active",
				this.picker_class = "h-uni-picker",
				setTimeout(() =>{
					this.mask_class = "h-uni-mask";
					this.mask_style = "display: none;"
				}, 250);
			},
			
			change(key) {
				if(key === null || key === undefined) {
					uni.showModal({
						title: "系统提示",
						content: "选中内容有误，请重新选择！",
						showCancel: false,
					});
					return;
				}
				
				this.value = key;
				this.$emit("change", key);
				this.hide();
			}
		},
		components: {
			faIcon
		}
	}
</script>

<style scoped>
	.h-uni-mask{
		position: fixed;
		z-index: 999;
		top: 0;
		right: 0;
		left: 0;
		bottom: 0;
		background: rgba(0,0,0,.6);
	}
	.h-uni-fade-enter-active,
	.h-uni-fade-leave-active {
		-webkit-transition-duration: .25s;
		transition-duration: .25s;
		-webkit-transition-property: opacity;
		transition-property: opacity;
		-webkit-transition-timing-function: ease;
		transition-timing-function: ease
	}
	.h-uni-fade-enter-active{
		opacity: 1
	}
	.h-uni-fade-leave-active {
		opacity: 0
	}
	.h-uni-picker{
		position: fixed;
		left: 0;
		bottom: 0;
		transform: translateY(100%);
		backface-visibility: hidden;
		z-index: 999;
		width: 100%;
		background-color: #efeff4;
		visibility: hidden;
		transition-property: transform,visibility;
		transition-duration: .3s,.3s;
	}
	.h-uni-picker.h-uni-picker-toggle{
		visibility: visible;
		transform: translate(0);
	}
	.h-uni-picker .h-uni-picker-header{
		display: block;
		position: relative;
		text-align: center;
		width: 100%;
		height: 45px;
		background-color: #fff;
		line-height: 45px;
		border-bottom: 1px solid #ccc;
	}
	.h-uni-picker .h-uni-picker-header .h-uni-picker-close{
		position: absolute;
		right: 0;
		top: 0;
		line-height: 45px;width: 45px;
		text-align: center;
		
	}
	.h-uni-picker .h-uni-picker-action{
		display: block;
		max-width: 50%;
		top: 0;
		height: 100%;
		box-sizing: border-box;
		padding: 0 14px;
		font-size: 17px;
		line-height: 45px;
		overflow: hidden;
	}
	.h-uni-picker .h-uni-picker-action.h-uni-picker-action-cancel{
		float: left;
		color: #888;
	}
	.h-uni-picker .h-uni-picker-action.h-uni-picker-action-confirm{
		float: right;
		color: #007aff;
	}
	.h-uni-picker .h-uni-picker-content{
		position: relative;
		display: block;
		width: 100%;
		height: 238px;
		background-color: #fff;
		padding: 10px;
	}
	.h-uni-picker .h-uni-picker-content .h-uni-picker-list{
		display: flex;
		justify-content: space-between;
		align-items: center;
		line-height: 54px;
		border-bottom: 1px solid #eee;
	}
</style>
