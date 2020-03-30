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
		<view class="order_view">
			<view class="order">
				<view class="order_top">
					<view class="order_top_left">
						<text>01#</text>
						<text>图书馆A柜 15格</text>
					</view>
					<view class="order_top_right">
						配送时间段：早餐
					</view>
				</view>
				<view class="order_commodity">
					<view class="order_player">
						用户名：2020021555
					</view>
					<view class="commodity_view">
						<view class="name">油条</view>
						<view class="num">X1</view>
						<view class="cash">10</view>
					</view>
				</view>
				<view class="order_btn_view">
					<view class="order_btn">取消订单</view>
					<view class="order_btn order_btn1">打印订单</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default {
		components: {
			navbar
		},
		data() {
			return{}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	page {
		background: #F5F5F5;
	}

	.top_view {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 30upx 32upx 0;
		box-sizing: border-box;
	}

	.top_left {
		display: flex;
		align-items: center;
		font-size: 32upx;
		color: #999999;
	}

	.printing_btn {
		font-size: 28upx;
		color: #fff;
		border-radius: 34upx;
		padding: 10upx 24upx;
		
		background:linear-gradient(268deg,rgba(255,55,78,1) 0%,rgba(255,93,55,1) 100%);
		margin-left: 40upx;
	}

	.icon-dayinji {
		font-size: 44upx;
		color: #999999;
	}
	/* 订单 */
	.order{
		display: flex;
		flex-direction: column;
		width: 710upx;
		margin: 30upx auto 0;
		background: #FFFFFF;
		border-radius: 24upx;
		overflow: hidden;
		color: #333333;
		font-size: 28upx;
	}
	.order_top{
		width: 100%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		padding: 20upx 32upx;
		box-sizing: border-box;
		color: #FFFFFF;
		background:linear-gradient(0deg,rgba(255,55,78,1) 0%,rgba(255,153,122,1) 100%);
		
		border-bottom: 1upx solid #F5F5F5;
	}
	.order_commodity{
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		width: 100%;
		padding: 20upx 32upx;
		box-sizing: border-box;
		border-bottom: 2upx solid #F5F5F5;
	}
	.commodity_view{
		width: 100%;
		display: flex;
		flex-direction: row;
		align-items: center;
		text-align: center;
	}
	.name{
		width: 50%;
	}
	.num{
		width: 25%;
	}
	.cash{
		width: 25%;
	}
	.order_btn_view{
		width: 100%;
		padding: 10upx 32upx;
		box-sizing: border-box;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
	}
	.order_btn{
		width: 140upx;
		height: 48upx;
		border-radius: 24upx;
		background: #eeeeee;
		color: #333;
		font-size: 24upx;
		line-height: 48upx;
		text-align: center;
	}
	.order_btn1{
		color: #FFFFFF;
		background: linear-gradient(270deg, rgba(249, 128, 80, 1) 1%, rgba(255, 186, 89, 1) 100%) !important;
	}
</style>
