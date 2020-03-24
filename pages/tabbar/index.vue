<template>
	<view class="page">
		<view style="font-size: 0;"><image class="index_img" src="/static/index_bg.png" mode="aspectFill"></image></view>
		<view class="btn_view">
			<view class="btn" @click="goClick('../order/orderProcessing')">
				<view class="icons_view"><span class="iconfont icon-wodedingdan icons"></span></view>
				<view class="btn_text">订单处理</view>
			</view>
			<view class="btn" @click="goClick('../order/dishesData')">
				<view class="icons_view icons_view1"><span class="iconfont icon-shuju-heise icons"></span></view>
				<view class="btn_text">菜品数据</view>
			</view>
			<view class="btn" @click="goClick('../cabinet/cabinet')">
				<view class="icons_view icons_view2"><span class="iconfont icon-zhongduanbangdingsvg icons"></span></view>
				<view class="btn_text">柜子管理</view>
			</view>
		</view>
		<view class="btn_view">
			<view class="btn" @click="goClick('../commodity/commodityAdd')">
				<view class="icons_view icons_view3"><span class="iconfont icon-fuwushangruwangsvg icons"></span></view>
				<view class="btn_text">商品管理</view>
			</view>
			<view class="btn" @click="goClick('../commodity/menuAdd')">
				<view class="icons_view icons_view4"><span class="iconfont icon-shanghuruwangsvg icons"></span></view>
				<view class="btn_text">菜单安排</view>
			</view>
			<view class="btn" @click="goClick('../commodity/commodityComment')">
				<view class="icons_view icons_view5"><span class="iconfont icon-lishijiangli icons"></span></view>
				<view class="btn_text">菜品评价</view>
			</view>
		</view>
		<view class="btn_view btn_view1">
			<view class="btn" @click="goClick('../data/manageData')">
				<view class="icons_view icons_view6"><span class="iconfont icon-tixianjilu icons"></span></view>
				<view class="btn_text">经营数据</view>
			</view>
			<view class="btn" @click="goClick('../notice/notice')">
				<view class="icons_view icons_view7"><span class="iconfont icon-xiaoxizhongxinsvg icons"></span></view>
				<view class="btn_text">通知管理</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				orders:['','','','','','','','']
			}
		},
		onLoad() {
			
		},
		methods:{
			goClick(url){
				uni.navigateTo({
					url: url
				})
			}
		}
	}
</script>

<style>
	page{
		background: #FFFFFF;
	}
	
	.index_img{
		width: 100%;
		height: 319upx;
		
	}
	.btn_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		padding: 80upx 120upx 0;
	}
	.btn{
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.btn:nth-of-type(5){
		margin-right: 0;
	}
	.icons_view{
		background:linear-gradient(0deg,rgba(44,176,252,1) 0%,rgba(76,219,255,1) 100%);
		width: 80upx;
		height: 80upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 50%;
	}
	.btn_view1{
		justify-content: space-around;
	}
	.icons_view1{
		background:linear-gradient(0deg,rgba(244,74,111,1) 0%,rgba(240,141,141,1) 100%);
	}
	.icons_view2{
		background:linear-gradient(0deg,rgba(140,27,228,1) 0%,rgba(212,132,255,1) 100%);
	}
	.icons_view3{
		background:linear-gradient(180deg,rgba(251,133,52,1) 0%,rgba(249,78,37,1) 100%);
	}
	.icons_view4{
		background:linear-gradient(180deg,rgba(240,209,93,1) 0%,rgba(243,180,81,1) 100%);
	}
	.icons_view5{
		background: linear-gradient(180deg,rgba(254,101,87,1) 0%,rgba(247,29,30,1) 100%);
	}
	.icons_view6{
		background: linear-gradient(270deg,rgba(251,51,82,1) 0%,rgba(244,92,139,1) 100%);
	}
	.icons_view7{
		background: linear-gradient(90deg,rgba(124,141,254,1) 0%, rgba(83,97,238,1) 100%);
	}
	.btn_text{
		font-size: 24upx;
		line-height: 1;
		padding-top: 14upx;
	}
	.icons{
		font-size: 44upx;
		line-height: 1;
		color: #FFFFFF;
	}
</style>
