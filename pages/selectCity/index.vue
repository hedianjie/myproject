<template>
	<view class="content">
		<!-- 头部搜索 -->
		<search-city @selected="submit"></search-city>
		<!-- <view class="usually-city">
			
		</view> -->
		<!-- 底部 -->
		<indexed-list :options="options" :showSelect="false" @click="submit"></indexed-list>
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
		padding-top: 56px
	}
</style>
