<template>
	<view class="content">
		<view class="address-list" v-for="(item, index) in list">
			<view class="address-list-left">
				<view class="address-header">
					{{item.address_name}}
					<view v-if="item.tag_type == 0" class="address-tag tag-0">学校</view>
					<view v-else-if="item.tag_type == 1" class="address-tag tag-1">家</view>
					<view v-else-if="item.tag_type == 2" class="address-tag tag-2">单位</view>
				</view>
				<view class="address-info">{{item.address_info}}</view>
				<view class="address-information">
					<span class="m-r-15"><fa-icon type="user" size="14" color="#999999" margin="0 5px 0 0"></fa-icon>{{item.name}}</span>
					<span><fa-icon type="phone " size="14" color="#999999" margin="0 5px 0 0"></fa-icon>{{item.phone}}</span>
				</view>
			</view>
			<navigator url="../createAddress/index" class="address-list-right">
				<fa-icon type="edit" size="22" color="#999999"></fa-icon>
			</navigator>
		</view>
		
		<navigator url="../createAddress/index" class="add-address">
			<fa-icon type="plus" size="18" color="#007AFF" margin="0 5px 0 0"></fa-icon>添加常用地址
		</navigator>
	</view>
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	export default {
		onLoad(option) {
			// 是否选择 或者查看地址列表 通过路由参数
			uni.setNavigationBarTitle({
				title: "查看地址"
			});
		},
		
		data() {
			return {
				list: [
					{
						id: 1,
						address_name: "天盛名都B座",
						address_info: "2号楼 3单元 1206",
						tag_type: 1, // -1 -> 无标签 0 -> 学校 1-> 家 2-> 单位
						name: "何先生",
						phone: "15564402010"
					},
					{
						id: 1,
						address_name: "天盛名都天盛名都天盛名都天盛名都天盛名都天盛名都天盛名都B座",
						address_info: "2号楼 3单元 1206",
						tag_type: 2, // -1 -> 无标签 0 -> 学校 1-> 家 2-> 单位
						name: "何先生",
						phone: "15564402010"
					}
				]
			}
		},
		methods: {
			
		},
		
		components: {
			faIcon
		}
	}
</script>

<style scoped>
	page{
		background: #ffffff;
	}
	.content{
		padding-bottom: 60px;
	}
	.address-list {
		position: relative;
		background: #FFFFFF;
		padding: 20px 0;
		padding-right: 40px;
		margin: 0 12px;
		border-bottom: 1px solid #ddd;
	}
	.address-list .address-list-left .address-header{
		font-size: 16px;
		font-weight: bold;
		margin-bottom: 7px;
	}
	.address-list .address-list-left .address-info{
		font-size: 14px;
		margin-bottom: 7px;
	}
	.address-list .address-list-left .address-information{
		font-size: 14px;
		color: #999999;
	}
	.address-list .address-list-right{
		position: absolute;
		top: 50%;
		right: 0;
		width: 40px;
		text-align: center;
		margin-top: -11px;
	}
	.address-list .address-list-left .address-tag{
		margin-left: 10px;
		display: inline-block;
		font-size: 12px;
		padding: 1px 5px;
		font-weight: 400;
		color: #fff;
		border-radius: 2px;
	}
	.address-tag.tag-0{
		background: #28A745;
	}
	.address-tag.tag-1{
		background: #28A745;
	}
	.address-tag.tag-2{
		background: #28A745;
	}
	.add-address{
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 60px;
		line-height: 60px;
		text-align: center;
		color:#007AFF;
		border-top: 1px solid #e1e1e1;
		font-size: 16px;
		background: #f1f1f1;
	}
</style>
