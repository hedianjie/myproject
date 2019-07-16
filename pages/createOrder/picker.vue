<template>
	<picker :range="range" @change="submit" @columnchange="columnchange" :value="value"  mode="multiSelector" >
		<slot name="picker"></slot>
	</picker>
</template>

<script>
	export default {
		props: {
			defaultTime: {
				type: String,
				default() {
					return "00:00";
				}
			},
			
			defaultType: {
				type: Number,
				default() {
					return 0;
				}
			},
			
			defaultDate: {
				type: Number,
				default() {
					return 0;
				}
			}
		},
		data() {
			return {
				range: [
					["立即到达", "约定时间"],
					["今天", "明天"],
					["00点", "01点", "02点", "03点", "04点", "05点", "06点", "07点", "08点", "09点", "10点", "11点", "12点", "13点", "14点", "15点", "16点", "17点", "18点", "19点", "20点", "21点", "22点", "23点"],
					["00分", "01分", "02分", "03分", "04分", "05分", "06分", "07分", "08分", "09分", "10分", "11分", "12分", "13分", "14分", "15分", "16分", "17分", "18分", "19分", "20分", "21分", "22分", "23分", "24分", "25分", "26分", "27分", "28分", "29分", "30分", "31分", "32分", "33分", "34分", "35分", "36分", "37分", "38分", "39分", "40分", "41分", "42分", "43分", "44分", "45分", "46分", "47分", "48分", "49分", "50分", "51分", "52分", "53分", "54分", "55分", "56分", "57分", "58分", "59分"]
				],
				
				/**
				 * 第一项 0->立即到达 1->约定时间
				 * 第二项 0->今天 1->明天
				 * 第三项 时
				 * 第四项 分
				 */
				value: [0, 0, 0, 0]
			}
		},
		mounted() {
			this.init();
		},
		methods: {
			/**
			 * 初始化
			 */
			init() {
				const {defaultTime, defaultDate, defaultType} = this;
				let def1, def2, def3, def4;
				
				// 第一项
				def1 = defaultType;
				def1 == 0 ? this.range.splice(1 ,1, ["今天"]) : this.range.splice(1 ,1, ["今天", "明天"]);
				// 第二项
				def2 = defaultDate;
				
				// 3,4
				[def3, def4] = defaultTime.split(":");
				
				this.value = [Number(def1), Number(def2), Number(def3), Number(def4)];
			},
			/**确定
			 * @param {Object} e回调接收参数	
			 */
			submit(e) {
				this.value = [...e.detail.value];
				const h = this.range[2][this.value[2]];
				const m = this.range[3][this.value[3]];
				
				this.$emit("arriveTime", {
					time: parseInt(h) + ":" + parseInt(m),
					type: this.value[0],
					date: this.value[1],
				});
			},
			/**变更回调
			 * @param {Object} e回调接收参数	
			 */
			columnchange(e) {
				const {column, value} = e.detail;
				if(column == 0) {
					if(value !== this.value[0]) {
						value == 0 ? this.range.splice(1 ,1, ["今天"]) : this.range.splice(1 ,1, ["今天", "明天"]);
						this.value.splice(0, 1, value);
					}
				}
			},
		}
	}
</script>

<style>
</style>
