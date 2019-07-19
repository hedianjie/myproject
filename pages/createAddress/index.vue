<template>
	<view class="content">
		<view class="form-horizontal">
			<view class="form-group">
				<view class="label">联系人</view>
				<input :type="'text'" maxlength="10" class="form-control" value="" placeholder="姓名" v-model="name"/>
			</view>
			<view class="form-group bar">
					<view class="label"></view>
					<view class="form-control">
						<span class="tag tag-sm">先生</span>
						<span class="tag tag-sm">女士</span>
					</view>
					<!-- <input type="text" class="form-control" value="" placeholder="请输入联系人"/> -->
			</view>
		</view>
	</view>
</template>

<script>
	import faIcon from "../../components/kilvn-fa-icon/fa-icon.vue";
	export default {
		onLoad(option) {
			// 通过路由参数决定导航栏文字 编辑或者新建
			uni.setNavigationBarTitle({
				title: "添加地址"
			})
		},
		
		data() {
			return {
				name: "",
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.bar{
		border-color: #eeeeee;
	}
	page{
		background: #F8F9FA;
	}
	.tag{
		border: 1px solid #eee;
		border-radius: 3px;
		color: #999999;
		font-size: 14px;
	}
	.form-horizontal{
		padding: 0 12px;
		background: #FFFFFF;
	}
	.form-group {
		padding: 8px 0;
	}
	.form-group {
		display: flex;
		align-items: flex-start;
	}
	.form-group .label{
		height: 44px;
		font-size: 15px;
		color: #333333;
		line-height: 44px;
		font-weight: bold;
		margin-right: 10px;
		width: 76px;
		text-align: right;
	}
	.form-group .form-control{
		height: 44px;
		width: 100%;
		min-height: auto;
		border: none;
		outline: none;
		font-size: 14px;
	}
</style>
