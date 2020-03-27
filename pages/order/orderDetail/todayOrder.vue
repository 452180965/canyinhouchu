<template>
	<view class="page">
		<navbar title="当日订单" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="top_view">
			<view class="top_left">
				<text>该餐点所有订单:</text>
				<view class="printing_btn">打印</view>
			</view>
			<span class="iconfont icon-dayinji"></span>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default {
		components: {
			navbar
		},
		data(){
			
		},
		onLoad() {
			
		},
		methods:{
			
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.top_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 30upx  32upx 0;
		box-sizing: border-box;
	}
	.top_left{
		display: flex;
		align-items: center;
		font-size: 32upx;
		color: #999999;
	}
	.printing_btn{
		font-size: 28upx;
		color: #fff;
		border-radius: 14upx;
		padding: 10upx 20upx;
		background: #FFBA59;
		margin-left: 40upx;
	}
	.icon-dayinji{
		font-size: 44upx;
		color: #999999;
	}
</style>
