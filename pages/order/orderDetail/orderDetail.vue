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
			<view class="time_text">
				柜子筛选:
			</view>
			<picker mode="selector" :range="array" @change="pickerClick" @cancel="cancelClick">
				<view>{{arrayText}} </view>
			</picker>
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
			return{
				array:['1','2'],
				arrayText:'1'
			}
		},
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
	picker{
		margin-left: 20upx;
	}
</style>
