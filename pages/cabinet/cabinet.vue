<template>
	<view class="page">
		<navbar title="柜子管理" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="search">
			<view>地点:</view>
			<picker class="picker" mode="selector" @change="pickerClick"  :range="key" >
				<view class="time_input">{{key[pickType]}} </view>
			</picker>
			<view>机柜:</view>
			<picker class="picker" mode="selector" @change="pickerClick1" :range="key">
				<view class="time_input">{{key1[pickType1]}}</view>
			</picker>
			<view class="search_btn">查询</view>
		</view>
		<view class="guizi_view">
			<image class="guizi_img" src="../../static/guizi.png"></image>
			<view class="name">
				<text id="text">图书馆</text>
				<text>温度:60℃</text>
			</view>
			<view class="gezi_view">
				
				<view class="gezi" v-for="(item,index) in gezi" :key="index">{{item}}</view>
			</view>
		</view>
		<view class="btn_view">
			<view class="btn">全部打开</view>
			<view class="btn btn1">打开柜门</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		components:{
			navbar
		},
		data(){
			return{
				gezi:['B01','B02','B03','B04','','','','','','','','','','','','','','','','','','','','','','',''],
				key:['全部','图书馆'],
				key1:['全部','A柜'],
				pickType:0,
				pickType1:0
			}
		},
		onLoad() {
			
		},
		methods:{
			pickerClick(e){
				this.pickType = e.detail.value
			},
			pickerClick1(e){
				this.pickType1 = e.detail.value
			}
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.guizi_view{
		width: 100%;
		position: relative;
		display: flex;
		flex-direction: row;
		justify-content: center;
		height: 800upx;
	}
	.guizi_img{
		width: 580upx;
		height: 800upx;
		position: absolute;
		left: 50%;
		margin-left: -290upx;
		top: 80upx;
	}
	.gezi_view{
		width: 430upx;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		z-index: 1;
		padding-top: 170upx;
	}
	.gezi{
		width: 130upx;
		height: 60upx;
		background: #F5F5F5;
		margin-right: 20upx;
		margin-bottom: 10upx;
		border-radius: 10upx;
		font-size: 28upx;
		line-height: 60upx;
		color: #333333;
		text-align: center;
		
	}
	.gezi:nth-of-type(3n){
		margin-right: 0;
	}
	.name{
		position: absolute;
		top: 100upx;
		width: 520upx;
		left: calc(50% - 260upx);
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		font-size: 24upx;
	}
	#text{
		width: 180upx;
		height: 40upx;
		line-height: 40upx;
		background: #F5F5F5;
		text-align: center;
	}
	.search{
		display: flex;
		flex-direction: row;
		align-items: center;
		font-size: 32upx;
		padding-top: 30upx;
	}
	.picker{
		width: 120upx;
		height: 60upx;
		background: #FFFFFF;
		border: 1upx solid #999999;
		margin: 0 40upx;
		text-align: center;
		line-height: 60upx;
	}
	.search_btn{
		color: #FFFFFF;
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
		padding: 12upx 20upx;
		border-radius: 34upx;
		margin-left: 40upx;
		font-size: 28upx;
	}
	.btn_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 60%;
		margin: 120upx auto 0;
		font-size: 28upx;
		color: #333;
		
	}
	.btn{
		padding: 12upx 24upx;
		border: 1upx solid #999;
		background-color: #FFFFFF;
		border-radius: 34upx;
		
	}
	.btn1{
		border: 0;
		color: #FFFFFF;
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
	}
</style>
