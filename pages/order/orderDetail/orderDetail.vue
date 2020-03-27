<template>
	<view class="page">
		<navbar title="预定详情" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="time_view">
			<view class="time_text">配送时间:</view>
			<view class="time_input_view">
				<input type="text" class="time_input">
				<text>-</text>
				<input type="text" class="time_input">
			</view>
		</view>
		<view class="time_view time_view1">
			<view style="display: flex;align-items: center;">
				<view class="time_text">
					柜子筛选:
				</view>
				<view class="picker">
					<picker mode="selector" :range="array" @change="pickerClick" @cancel="cancelClick">
						<view>{{arrayText}} </view>
					</picker>
					<span class="iconfont icon-jiantou1"></span>
				</view>
			</view>
			<view class="search_btn">查询</view>
		</view>
		<view class="table_view">
			<view class="table_left_view">
				<view class="table">序号</view>
				<view class="table" v-for="(item,index) in table" :key="index">{{item.id}}</view>
			</view>
			<view class="table_center_view">
				<view class="table">菜品名称</view>
				<view class="table" v-for="(item,index1) in table" :key="index1">{{item.name}}</view>
			</view>
			<view class="table_right_view">
				<view class="table">份数</view>
				<view class="table" v-for="(item,index2) in table" :key="index2">{{item.type}}</view>
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
			return {
				array: ['1', '2'],
				arrayText: '1',
				table: [{
						id: '1',
						name: 'dd',
						type: '3'
					},
					{
						id: '1',
						name: 'dd',
						type: '3'
					},
					{
						id: '1',
						name: 'dd',
						type: '3'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			pickerClick(e) {
				console.log(e)
				this.arrayText = this.array[e.detail.value]
			},
		}
	}
</script>

<style>
	page {
		background-color: #F5F5F5;
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
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
	}

	/* 表格 */
	.table_view {
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 710upx;
		margin: 40upx auto 0;
		background: #F5F5F5;
	}

	.table_left_view {
		width: 15%;
		border-right: 1upx solid #999;
	}

	.table_center_view {
		width: 60%;
	}

	.table_right_view {
		width: 25%;
		border-left: 1upx solid #999999;
	}

	.table {
		width: 100%;
		height: 68upx;
		text-align: center;
		line-height: 68upx;
		font-size: 32upx;
		color: #333333;
	}

	.table:nth-last-of-type(2n) {
		background: #c5c5c5;
	}
</style>
