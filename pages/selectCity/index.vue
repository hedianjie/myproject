<template>
	<view class="content">
		<!-- 头部搜索 -->
		<search-city @selected="submit"></search-city>
		<!-- <view class="usually-city">
			
		</view> -->
		<!-- 底部 -->
		<view class="index-list-wrapper">
			<indexed-list :options="options" :showSelect="false" @click="submit"></indexed-list>
		</view>
	</view>
</template>

<script>
	import searchCity from "./searchCity.vue";
	import indexedList from "@/components/uni-indexed-list/uni-indexed-list.vue";
	import cityList from "@/components/city-all.js";
	export default {
		data() {
			return {
				options: cityList,
			}
		},
		methods: {
			// 提交
			submit(item) {
				if(item){
					console.log(item)
				}
			}
		},
		components: {
			indexedList,
			searchCity
		}
	}
</script>

<style>
	.content{
		position: fixed;
		height: calc(100% - var(--window-top));
		width: 100%;
		padding-top: 56px;
	}
	.index-list-wrapper{
		height: 100%;
	}
</style>
