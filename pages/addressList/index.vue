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
		background: #ffffff;;
	}
	.address-list {
		position: relative;
		background: #FFFFFF;
		padding: 40upx 0;
		padding-right: 80upx;
		margin: 0 24upx;
		border-bottom: 1px solid #ddd;
	}
	.address-list .address-list-left .address-header{
		font-size: 32upx;
		font-weight: bold;
		margin-bottom: 14upx;
	}
	.address-list .address-list-left .address-info{
		font-size: 28upx;
		margin-bottom: 14upx;
	}
	.address-list .address-list-left .address-information{
		font-size: 28upx;
		color: #999999;
	}
	.address-list .address-list-right{
		position: absolute;
		top: 50%;
		right: 0;
		width: 80upx;
		text-align: center;
		margin-top: -22upx;
	}
	.address-list .address-list-left .address-tag{
		margin-left: 20upx;
		display: inline-block;
		font-size: 24upx;
		padding: 2upx 10upx;
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
</style>
