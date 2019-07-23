<template>
	<view class="layout" :style="'height:' + (closeStatus ? 'calc(100% - var(--window-top))' : 0)">
		<view class="layout-header">
			<view class="header-main">
				<view class="search-city">
					<view class="search-city-content">长春市阿萨德</view>
					<view class="serach-city-icon"><fa-icon type="angle-down" size="12" color="#999999" style="0 0 0 5px"></fa-icon></view>
				</view>
				<!-- <fa-icon class="search-icon" type="search" size="22" color="#999999"></fa-icon> -->
				<input class="search-input" :type="'text'" value="" v-model="searchModel" placeholder="查找小区 / 写字楼 / 学校"/>
				<fa-icon v-show="closeStatus" class="search-close" @click="searchModel=''" type="close" size="22" color="#999999"></fa-icon>
			</view>
		</view>
		<scroll-view scroll-y="true" class="main" v-show="closeStatus">
			<!-- <view v-if="list.length" class="main-content">
				<view v-for="item in list" class="list-item" @click="submit(item)">{{item.name}}</view>
			</view> -->
			<!-- <view v-else class="list-none">没有要搜索的结果</view> -->
			<view class="list-none">没有要搜索的结果</view>

		</scroll-view>
	</view>
	
</template>

<script>
	import faIcon from "@/components/kilvn-fa-icon/fa-icon.vue";
	// import cityList from "@/components/city-all.js";
	export default {
		data() {
			return {
				searchModel: "",
				closeStatus: false,
				list: [],
			}
		},
		methods: {
			submit(item) {
				if(item) {
					this.$emit("selected", item);
					// 清空搜索
					this.searchModel = "";
				}
			}
		},
		components: {
			faIcon,
		},
		watch: {
			
			/**
			 * 根据搜索 删选城市
			 * @param {Object} val输入框值
			 */
			searchModel(val) {
				if (!val) {
					this.closeStatus = false;
					// 没有关键字 清空list
					this.list = [];
				}
				else {
					const ary = [];
					this.closeStatus = true;
					
					// 如果有关键字要搜索
					// for(let i = 0; i < cityList.length; i++) {
					// 	const curData = cityList[i].data;
					// 	 
					// 	if(curData.length) {
					// 		for(var j = 0 ; j < curData.length; j++) {
					// 			if(
					// 				curData[j].name.indexOf(val) != -1 ||  // 名字里有要搜索的关键字
					// 				curData[j].adcode.toString().indexOf(val) != -1		// 地区码中有要搜索的关键字
					// 			) {
					// 				ary.push(curData[j])
					// 			}
					// 		 
					// 		}
					// 	}
					// 	
					// }
					this.list = ary;
				}
				
				
			},
		}
	}
</script>

<style scoped>
	.layout{
		position: fixed;
		z-index: 20;
		top: 44px;
		left: 0;
		width: 100%;
		/* height: calc(100% - var(--window-top)); */
		background: #FFFFFF;
		padding: 10px 12px;
		padding-top: 56px;
		padding-bottom: 0;
	}
	.layout-header{
		position: absolute;
		top: 10px;
		left:0px;
		width: 100%;
		padding: 0 10px;
	}
	.layout-header .header-main{
		padding-left: 100px;
		padding-right: 36px;
		position: relative;
		height: 36px;
		background: #dddddd;
		border-radius: 36px;
	}
	.layout-header .search-city{
		line-height: 36px;
		left: 10px;
		top: 0;
		width: 50px;
		position: absolute;
		text-align: center;
		overflow: hidden;
		word-break: break-all;
		white-space: nowrap;
		text-overflow:ellipsis;
		font-size: 14px;
	}
	.layout-header:before{
		content: "";
		left: 105px;
		position: absolute;
		top: 5px;
		height: 26px;
		width: 1px;
		background: #999999;
	}
	.layout-header .search-input{
		width: 100%;
		padding: 5px 0;
		background: transparent;
		border: none;
		outline: none;
		height: 36px;
		font-size: 14px;
		position: relative;
	}
	.layout-header .search-close{
		position: absolute;
		right: 0;
		top: 0;
		width: 36px;
		line-height: 36px;
		text-align: center;
	}
	.main{
		height: 100%;
		padding-bottom: 10px;
	}
	.main .list-item{
		line-height: 36px;
		font-weight: bold;
		font-size: 16px;
	}
	.main .list-none{
		text-align: center;
		margin-top: 44px;
		color: #999999;
	}
</style>
