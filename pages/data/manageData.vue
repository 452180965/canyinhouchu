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
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		components:{
			navbar
		},
		onReady() {
			var timestamp = Date.parse(new Date())
			this.beginDate = this.toolUtil.getTimeStrOnlyDate(timestamp)
			this.lastDate = this.toolUtil.getTimeStrOnlyDate(timestamp)
		},
		data(){
			return{
				beginDate:'',
				lastDate:''
			}
		},
		onLoad() {
			
		},
		methods:{
			
		}
	}
</script>

<style>
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
</style>
