<template>
	<view class="content">
		
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
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	page{
		background: #F8F9FA;
	}

</style>
