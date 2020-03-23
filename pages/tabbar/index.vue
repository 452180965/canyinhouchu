<template>
	<view class="page">
		<view class="welcome">欢迎来到（第五中学）智能食堂</view>
		<view class="top_view">
			<view class="img_view"><image class="top_img" src="../../static/plant01.png" mode=""></image></view>
			<view class="address_view">
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		onLoad() {
			
		},
		methods:{
			
		}
	}
</script>

<style>
	page{
		background: #FFFFFF;
	}
	.welcome{
		width: 100%;
		text-align: center;
		font-size: 32upx;
	}
	.img_view{
		font-size: 0;
	}
	.top_img{
		width: 30upx;
		height: 40upx;
	}
</style>
