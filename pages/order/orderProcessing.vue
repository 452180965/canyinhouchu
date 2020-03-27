<template>
	<view class="page">
		<navbar title="订单处理" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="search_view" :style="{top:searchHeight + 'px'}">
			<view class="search">
				<span class='iconfont icon-sousuo'></span>
				<input class="search_input" type="text" value="" placeholder-class="placeholder" placeholder="请输入学号或订单号" />
			</view>
			<view class="search_btn">查询</view>
		</view>
		<view class="tab_view" :style='{top:tabHeight +"px"}'>
			<view class="tab_box">
				<view class="tab" v-for="(item,index) in tabText" :key="index" :class="{active:tabType==index}" @click="tabClick(index)">{{tabText[index]}}</view>
			</view>
		</view>
		<view class="kongHeights"></view>
		<view class="table_view">
			<view class="top_view" :style="{background:colorList[colorType]}">
				<view class="title">{{titles}}</view>
				<view class="detail_text" @click="detailClick">详情</view>
			</view>
			<view class="table">
				<view class="table_left">
					<span class="iconfont icon-wucan"></span>
					<view class="table_text">早餐</view>
				</view>
				<view class="table_left">
					<view class="table_num">100份</view>
					<span class="iconfont icon-jiantou"></span>
				</view>
			</view>
			<view class="table">
				<view class="table_left">
					<span class="iconfont icon-icon"></span>
					<view class="table_text">午餐</view>
				</view>
				<view class="table_left">
					<view class="table_num">100份</view>
					<span class="iconfont icon-jiantou"></span>
				</view>
			</view>
			<view class="table">
				<view class="table_left">
					<span class="iconfont icon-wancan"></span>
					<view class="table_text">晚餐</view>
				</view>
				<view class="table_left">
					<view class="table_num">100份</view>
					<span class="iconfont icon-jiantou"></span>
				</view>
			</view>
			<view class="table">
				<view class="table_left">
					<span class="iconfont icon-yexiao"></span>
					<view class="table_text">夜宵</view>
				</view>
				<view class="table_left">
					<view class="table_num">100份</view>
					<span class="iconfont icon-jiantou"></span>
				</view>
			</view>
			<view class="bottom_view" :style="{background:colorList[colorType]}">
				<view class="bottom_text">合计:1200份</view>
			</view>
		</view>
		<view class="bottom_tab_view">
			<view class="bottom_tab">当日订单</view>
			<view class="bottom_tab">预订单</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		onReady() {
			this.searchHeight = this.$store.state.kongHeight
			this.tabHeight = this.$store.state.kongHeight + 44
		},
		components:{
			navbar
		},
		data(){
			return{
				tabHeight:'',
				searchHeight:'',
				tabType:0,
				titles:"今日订单",
				tabText:['今日订单','明日订单','后日订单'],
				colorList:['#D6D6D6','#ff8f80','#9eb3ff','#fff560'],
				colorType:0
			}
		},
		onLoad() {
			
		},
		methods:{
			tabClick(type){
				if(this.tabType == type){
					return false
				}
				this.tabType = type
				this.titles = this.tabText[type]
				if(this.colorType<3){
					this.colorType++
				}else{
					this.colorType = 0
				}
			},
			detailClick(){
				uni.navigateTo({
					url:"orderDetail/orderDetail"
				})
			},
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.search_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 0 32upx;
		height: 88upx;
		box-sizing: border-box;
		background: #FFFFFF;
		position: fixed;
		left: 0;
	}
	.search{
		display: flex;
		align-items: center;
		border: 2upx solid #999999;
		border-radius: 34upx;
		height: 68upx;
		width: 500upx;
		padding: 0 20upx;
		box-sizing: border-box;
	}
	.icon-sousuo{
		color: #333333;
		padding-right: 10upx;
	}
	.search_input{
		color: #333333;
	}
	.placeholder{
		font-size: 32upx;
		color: #999999;
	}
	.search_btn{
		font-size: 32upx;
		color: #FFFFFF;
		width: 120upx;
		height: 68upx;
		border-radius: 34upx;
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
		text-align: center;
		line-height: 68upx;
	}
	/* tab */
	
	.tab_view {
		height: 68upx;
		width: 100%;
		background: #FFFFFF;
		position: fixed;
		left: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 9999999;
	}
	.tab_box{
		height: 48upx;
		border-radius: 64upx;
		background: #F5F5F5;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.tab{
		width: 180upx;
		font-size: 28upx;
		color: #333333;
		text-align: center;
		line-height: 48upx;
		height: 48upx;
		border-radius: 64upx;
	}
	.active{
		background: #FFBA59 !important;
		color: #FFFFFF !important;
	}
	.kongHeights{
		height: 156upx;
		width: 100%;
		opacity: 0;
	}
	/* 表格 */
	.table_view{
		width: 600upx;
		margin: 40upx auto 0;
		border-radius: 34upx;
		overflow: hidden;
	}
	.top_view{
		width: 100%;
		height: 98upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		padding: 0 32upx;
		box-sizing: border-box;
		background: #d6d6d6;
	}
	.title{
		font-size: 28upx;
		line-height: 1;
		color: #333333;
	}
	.detail_text{
		font-size: 28upx;
		color: #007AFF;
		line-height: 1;
		padding: 20upx 0 20upx 20upx;
	}
	.table{
		height: 108upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 0 32upx;
		box-sizing: border-box;
		border-bottom: 2upx solid #F5F5F5;
		background: #FFFFFF;
	}
	.table_left{
		display: flex;
		align-items: center;
	}
	.icon-wucan{
		font-size: 40upx;
		color: #167BBA;
	}
	.icon-icon{
		font-size: 40upx;
		color: #FF4D4C;
	}
	.icon-wancan{
		color: #0FC299;
		font-size: 40upx;
	}
	.icon-yexiao{
		color: #FFAF25;
		font-size: 40upx;
	}
	.table_text{
		font-size: 32upx;
		color: #333333;
		line-height: 1;
		padding-left: 20upx;
	}
	.table_num{
		font-size: 32upx;
		line-height: 1;
		color: #333333;
		padding-right: 20upx;
	}
	.icon-jiantou{
		line-height: 1;
		color: #999999;
	}
	.bottom_view{
		width: 100%;
		height: 98upx;
		padding: 0 32upx;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		background-color: #D6D6D6;
		box-sizing: border-box;
	}
	.bottom_text{
		font-size: 28upx;
		line-height: 1;
		color: #333333;
	}
	/* 表格 */
	/* 底部栏 */
	.bottom_tab_view{
		width: 100%;
		height: 88upx;
		background: #FFFFFF;
		position: fixed;
		bottom: 0;
		left: 0;
		box-shadow: 0 -10upx 20upx rgba(0,0,0,0.1);
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.bottom_tab{
		width: 50%;
		text-align: center;
		font-size: 28upx;
		border-right: 2upx solid #F5F5F5;
	}
</style>
