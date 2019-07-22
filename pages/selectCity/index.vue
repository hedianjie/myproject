<template>
	<view>
		<indexed-list :options="options" :showSelect="false" @click="bindClick"></indexed-list>
	</view>
</template>

<script>
	import indexedList from "@/components/uni-indexed-list/uni-indexed-list.vue";
	import cityList from "@/components/city-all.js";
	export default {
		data() {
			return {
				options: cityList,
			}
		},
		methods: {
			bindClick() {
				console.log(arguments)
			}
		},
		components: {
			indexedList,
		}
	}
</script>

<style>

</style>
