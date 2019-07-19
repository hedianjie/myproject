<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	*{
		box-sizing: border-box;
	}
	page{
		font-size: 16px;
	}
	.bar{
		border-bottom: 1px solid #dddddd !important;
	}
	.bar-top{
		border-top: 1px solid #dddddd !important;
	}
	.p-a{
	  position: absolute !important;
	}
	.p-r{
	  position: relative !important;
	}
	.p-f{
	  position: fixed;
	}
	.pull-none{
		float: none !important;
	}
	.pull-left{
		float: left !important;
	}
	.pull-right{
		float: right !important;
	}
	.t-a-l{
		text-align: left !important;
	}
	.t-a-c{
		text-align: center !important;
	}
	.t-a-right{
		text-align: right !important;
	}

	.d-i-b{
	  display: inline-block !important;
	}
	.d-i{
	  display: inline !important;
	}
	.d-b{
	  display: block !important;
	}
	.d-t{
	  display: table !important;
	}
	.d-t-c{
	  display: table-cell !important;
	}

	.v-a-t{
		vertical-align: top !important;
	}
	.v-a-m{
		vertical-align: middle !important;
	}
	.v-a-b{
		vertical-align: bottom !important;
	}
	.color-red{
		color: #E4564F !important;
	}
	.color-green{
		color: #77C646 !important;
	}
	.color-blue{
		color: #478FCA !important;
	}
	.color-yellow{
		color: #FF892A !important;
	}
	.color-purple{
		color: #9585BF !important;
	}
	.color-grey{
		color: #A0A0A0 !important;
	}
	.color-pink{
		color: #c14f66 !important;
	}
	.color-white{
		color: #ffffff !important;
	}
	.color-tip{
	  color: rgb(126, 127, 131) !important;
	}
	.color-black{
		color: #333333 !important;
	}
	.color-inherit{
	  color: inherit !important;
	}
	.f-s-0{
	  font-size: 0 !important;
	}
	.f-s-12,
	.f-s-xs{
		font-size: 12px !important;
	}
	.f-s-13{
		font-size: 13px !important;
	}
	.f-s-14,
	.f-s-sm{
		font-size: 14px !important;
	}
	.f-s-16{
		font-size: 16px !important;
	}
	.f-s-18{
		font-size: 18px !important;
	}
	.f-s-20{
		font-size: 20px !important;
	}
	.f-s-22{
		font-size: 22px !important;
	}
	.f-s-24,
	.f-s-lg{
		font-size: 24px !important;
	}
	.f-w-b{
	  font-weight: bold !important;
	}
	.m-l-0{
		margin-left: 0px !important;
	}
	.m-l-5{
		margin-left: 5px !important;
	}
	.m-l-10{
		margin-left: 10px !important;
	}
	.m-l-15{
		margin-left: 15px !important;
	}
	.m-l-20{
		margin-left: 20px !important;
	}
	.m-r-0{
		margin-right: 0px !important;
	}
	.m-r-5{
		margin-right: 5px !important;
	}
	.m-r-10{
		margin-right: 10px !important;
	}
	.m-r-15{
		margin-right: 15px !important;
	}
	.m-r-20{
		margin-right: 20px !important;
	}
	.m-t-0{
		margin-top: 0px !important;
	}
	.m-t-5{
		margin-top: 5px !important;
	}
	.m-t-10{
		margin-top: 10px !important;
	}
	.m-t-15{
		margin-top: 15px !important;
	}
	.m-t-20{
		margin-top: 20px !important;
	}
	.m-b-0{
		margin-bottom: 0px !important;
	}
	.m-b-5{
		margin-bottom: 5px !important;
	}
	.m-b-10{
		margin-bottom: 10px !important;
	}
	.m-b-15{
		margin-bottom: 15px !important;
	}
	.m-b-20{
		margin-bottom: 20px !important;
	}
	
	
	.p-l-0{
		padding-left: 0px !important;
	}
	.p-l-5{
		padding-left: 5px !important;
	}
	.p-l-10{
		padding-left: 10px !important;
	}
	.p-l-15{
		padding-left: 15px !important;
	}
	.p-l-20{
		padding-left: 20px !important;
	}
	.p-r-0{
		padding-right: 0px !important;
	}
	.p-r-5{
		padding-right: 5px !important;
	}
	.p-r-10{
		padding-right: 10px !important;
	}
	.p-r-15{
		padding-right: 15px !important;
	}
	.p-r-20{
		padding-right: 20px !important;
	}
	.p-t-0{
		padding-top: 0px !important;
	}
	.p-t-5{
		padding-top: 5px !important;
	}
	.p-t-10{
		padding-top: 10px !important;
	}
	.p-t-15{
		padding-top: 15px !important;
	}
	.p-t-20{
		padding-top: 20px !important;
	}
	.p-b-0{
		padding-bottom: 0px !important;
	}
	.p-b-5{
		padding-bottom: 5px !important;
	}
	.p-b-10{
		padding-bottom: 10px !important;
	}
	.p-b-15{
		padding-bottom: 15px !important;
	}
	.p-b-20{
		padding-bottom: 20px !important;
	}
</style>
