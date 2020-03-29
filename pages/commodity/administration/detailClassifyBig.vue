<template>
	<view class="page">
		<navbar title="选择分类" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="title">大类</view>
		<view class="classify_view">
			<view class="classify" :class="bigType==index?'active':''" v-for="(item,index) in classify" :key="index" @click="typeClick(index)">
				<text>{{item.name}}</text>
				<span class="iconfont icon-sggg" v-if="bigType==index"></span>
			</view>
		</view>
		<view class="title">小类</view>
		<view class="classify_view">
			<view class="classify" :class="smallType==index?'active':''" v-for="(item,index) in classify" :key="index" @click="typeClick1(index)">
				<text>{{item.name}}</text>
				<span class="iconfont icon-sggg" v-if="smallType==index"></span>
			</view>
		</view>
		<view class="comfire_btn" @click="comfireClick">完成</view>
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
				bigType: '',
				smallType: '',
				comfire:false,
				classify:[
					{
						name: '套餐',
						id: '1'
					},
					{
						name: '自选餐',
						id:'2'
					},
					]
			}
		},
		onLoad() {
			
		},
		onUnload() {
			let pages = getCurrentPages()
			if(this.comfire){
				
				let prevPage = pages[pages.length - 1]
				
				prevPage.$vm.classify = this.classify
				prevPage.$vm.bigType = this.bigType + 1
				prevPage.$vm.smallType = this.smallType + 1
				
			}
		},
		methods:{
			typeClick(index){
				this.bigType = index
			},
			typeClick1(index){
				this.smallType = index
			},
			comfireClick(){
				this.comfire = true
				uni.navigateBack({
					
				})
			},
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.classify{
		width: 100%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		padding: 0 24upx;
		height: 78upx;
		background: #FFFFFF;
		font-size: 32upx;
		color: #333333;
		position: relative;
		box-sizing: border-box;
	}
	.classify::after{
		width: 702upx;
		height: 1upx;
		background: #F5F5F5;
		content: '';
		position: absolute;
		bottom: 0;
		left: calc(50% - 351upx);
	}
	.classify:last-of-type::after{
		height: 0;
	}
	.icon-sggg{
		color: #FFBA59;
		font-size: 36upx;
	}
	.active text{
		color: #FFBA59;
	}
	.title{
		font-size: 36upx;
		color: #333333;
		padding-top: 20upx;
		padding-bottom: 20upx;
	}
	.comfire_btn{
		width: 600upx;
		height: 78upx;
		font-size: 32upx;
		line-height: 78upx;
		text-align: center;
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
		color: #FFFFFF;
		margin: 40upx auto 0;
		border-radius: 44upx;
	}
</style>
