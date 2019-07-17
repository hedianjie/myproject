<template>
	<view class="content">
		<view class="wrapper">
			<textarea placeholder="请输入备注信息"  maxlength="50" :value="value"></textarea>
			<view class="impose">10/50</view>
		</view>
		<view class="wrapper">
			<button type="primary"><fa-icon type="check-circle" margin="0 5px 0 0" size="18" color="#ffffff"></fa-icon>保存备注信息</button>
		</view>
	</view>
</template>

<script>
	import faIcon from "../../components/kilvn-fa-icon/fa-icon.vue";
	export default {
		data() {
			return {
				value: "",
			}
		},
		methods: {
			
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
	.wrapper{
		padding: 20px 12px;
		padding-bottom: 0;
		position: relative;
	}
	.wrapper textarea{
		width: 100%;
		background: #fff;
		border: 1px solid #ccc;
		border-radius: 5px;
		height: 300upx;
		background: #f1f1f1;
		padding: 6px;
	}
	.wrapper .impose{
		position: absolute;
		right: 18px;
		bottom: 7px;
		font-size: 14px;
		color: #999999;
	}
</style>
