<template>
	<view class="page">
		<navbar title="经营数据" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="time_view">
			<view class="time_text">时间:</view>
			<view class="time_input_view">
				<picker mode="date" @change="pickerClick1" @cancel="cancelClick">
					<view class="time_input">{{beginDate}} </view>
				</picker>
				<text>-</text>
				<picker mode="date" @change="pickerClick2" @cancel="cancelClick">
					<view class="time_input">{{lastDate}} </view>
				</picker>
			</view>
			<view class="search_btn">查询</view>
		</view>
		<view class="today_view">
			<view class="today_title">今日营业统计</view>
			<view class="today_table_view">
				<view class="today_table">
					<view class="table_title">当日单</view>
					<view class="table_num">58单</view>
				</view>
				<view class="today_table">
					<view class="table_title">金额</view>
					<view class="table_num1">100元</view>
				</view>
				<view class="today_table">
					<view class="table_title">预定单</view>
					<view class="table_num">58单</view>
				</view>
				<view class="today_table">
					<view class="table_title">金额</view>
					<view class="table_num1">100元</view>
				</view>
			</view>
		</view>
		<view class="table_view">
			<view class="table">日期</view>
			<view class="table table1">当日单</view>
			<view class="table">金额</view>
			<view class="table table1">预订单</view>
			<view class="table">金额</view>
			<view class="table">退单</view>
			<view class="table">退款</view>
		</view>
		<view class="table_view table_view1">
			<view class="table">1</view>
			<view class="table table1 table_n">11</view>
			<view class="table table_n">1111</view>
			<view class="table table1 table_n">1111</view>
			<view class="table table_n">11</view>
			<view class="table table_n">11111</view>
			<view class="table table_n">111</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default {
		components: {
			navbar
		},
		onReady() {
			var timestamp = Date.parse(new Date())
			this.beginDate = this.toolUtil.getTimeStrOnlyDate(timestamp)
			this.lastDate = this.toolUtil.getTimeStrOnlyDate(timestamp)
		},
		data() {
			return {
				beginDate: '',
				lastDate: ''
			}
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

	.time_view {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding-top: 20upx;
		padding-left: 24upx;
	}

	.time_view1 {
		padding-top: 40upx;
		justify-content: space-between;
		width: 70%;
	}

	.time_input_view {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.time_text {
		font-size: 28upx;
		line-height: 1;
	}

	.time_input {
		width: 190upx;
		height: 48upx;
		border: 1upx solid #999999;
		font-size: 28upx;
		text-align: center;
		margin: 0 20upx;
		line-height: 48upx;
		background: #FFFFFF;
	}

	.picker {
		height: 60upx;
		margin-left: 20upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 160upx;
		padding: 0 10upx 0 20upx;
		box-sizing: border-box;
		border: 1upx solid #999;
		color: #333333;
		font-size: 28upx
	}

	.icon-jiantou1 {
		font-size: 28upx;
		color: #999;
		margin-top: 6upx;
	}

	.search_btn {
		font-size: 32upx;
		color: #FFFFFF;
		padding: 10upx 24upx;
		border-radius: 34upx;
		background: linear-gradient(270deg, rgba(249, 128, 80, 1) 1%, rgba(255, 186, 89, 1) 100%);
	}

	/* 今日 */
	.today_view {
		width: 710upx;
		display: flex;
		flex-direction: column;
		margin: 40upx auto 0;
	}

	.today_title {
		font-size: 32upx;
		color: #FFFFFF;
		background: #FFBA59;
		width: 100%;
		padding: 20upx 24upx;
		box-sizing: border-box;
		border-top-left-radius: 34upx;
		border-top-right-radius: 34upx;
	}

	.today_table_view {
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 100%;
		background: #FFFFFF;
	}

	.today_table {
		width: 25%;
		display: flex;
		flex-direction: column;
		align-items: center;
		font-size: 26upx;
		padding: 16upx 0;
		color: #333333;
		position: relative;
	}

	.today_table::after {
		content: '';
		height: 60upx;
		width: 4upx;
		background: #F1F1F1;
		right: 0;
		position: absolute;
		top: calc(50% - 30upx);
	}

	.today_table:last-of-type::after {
		width: 0;
	}

	.table_title {
		font-size: 24upx;
		color: #999999;
		padding-bottom: 10upx;
	}

	.table_num1 {
		color: #FFBA59;
	}
	.table_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 710upx;
		margin: 40upx auto 0;
		font-size: 28upx;
		background: #FFFFFF;
	}
	.table_view1{
		margin-top: 0 !important;
	}
	.table{
		height: 68upx;
		line-height: 68upx;
		text-align: center;
		width: 14%;
		border-right: 1upx solid #F5F5F5;
	}
	.table_view:nth-of-type(2n){
		background: #C5C5C5;
	}
	.table1{
		width: 15%;
	}
	.table_date{
		width: 14%;
		color: #333333;
		text-align: center;
	}
	.table_n{
		color: #777777 !important;
	}
</style>
