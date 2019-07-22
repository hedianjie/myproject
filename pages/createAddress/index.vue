<template>
	<view class="content">
		<view class="form-horizontal">
			
			<view class="form-group form-group-name">
				<view class="label">联系人</view>
				<input :type="'text'" maxlength="10" class="form-control" value="" placeholder="姓名" v-model="name"/>
			</view>
			
			<view class="form-group form-group-sex bar bar-top">
					<view class="label"></view>
					<view class="form-control">
						<span class="tag tag-sm m-r-15">先生</span>
						<span class="tag tag-sm">女士</span>
					</view>
			</view>
			
			<view class="form-group form-group-phone bar">
				<view class="label">电话</view>
				<input :type="'text'" maxlength="10" class="form-control" value="" placeholder="手机号码" v-model="phone"/>
			</view>
			
			<navigator url="../selectCity/index" class="form-group form-group-phone bar">
				<view class="label">地址</view>
				<input :type="'text'" maxlength="10" class="form-control" value="" placeholder="选择常用地址" v-model="address"/>
				<view class="form-icon"><fa-icon type="angle-right" size="24" color="#999999"></fa-icon></view>
			</navigator>
			
			<view class="form-group form-group-phone bar">
				<view class="label">门牌号</view>
				<input :type="'text'" maxlength="10" class="form-control" value="" placeholder="例:5号楼203室" v-model="address"/>
			</view>
			
			<view class="form-group form-group-phone">
				<view class="label">标签</view>
				<view class="form-control">
					<span class="tag tag-sm m-r-15">家</span>
					<span class="tag tag-sm m-r-15">公司</span>
					<span class="tag tag-sm">学校</span>
				</view>
			</view>
			
		</view>
		<view class="form-horizontal">
			<button type="primary" class="m-t-20">保存</button>
			<button type="default" class="m-t-20">删除</button>
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
				phone: "",
				address: "",
				sex: 1, // 1->先生 0->女士
				tag: 1, // 0->家 1->公司 2->学校
			}
		},
		methods: {
			
		},
		components:{
			faIcon
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
		padding: 5px 20px;
		line-height: 14px;
	}
	.form-horizontal{
		padding: 0 12px;
	}
	.form-group {
		padding: 8px 0;
		display: flex;
		align-items: flex-start;
		padding-right: 30px;
		line-height: 34px;
		position: relative;
		background: #ffffff;
	}
	.form-group .label{
		height: 34px;
		font-size: 15px;
		color: #333333;
		line-height: 34px;
		font-weight: bold;
		margin-right: 20px;
		width: 74px;
		text-align: right;
	}
	.form-group .form-control{
		height: 34px;
		width: 100%;
		min-height: auto;
		border: none;
		outline: none;
		font-size: 15px;
	}
	.form-group .form-icon{
		position: absolute;
		line-height: 34px;
		right: 12px;
		top: 8px;
	}
</style>
