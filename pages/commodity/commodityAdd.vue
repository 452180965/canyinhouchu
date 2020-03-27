<template>
	<view class="page">
		<navbar title="商品管理" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		
		<view class="big_view">
				<scroll-view class="scrollY" scroll-y="true" :style="{height: tabHeight + 'px'}">
					<view class="scroll1" v-for="(item,index) in classifyList" :key='index' :class="index==indexs?'scroll2':''" @click="classifyClick(index)">{{item}}</view>
				</scroll-view>
				<scroll-view class="scrollX" scroll-y="true" :style="{height: tabHeight + 'px'}">
					<view class="scroll3" v-for="(item,index1) in classifyList" :key='index1'>{{item}}</view>
				</scroll-view>
		</view>
		<view class="bottom_view">
			<view class="bottom_tab">
				<span class="iconfont icon-fenlei"></span><text>管理分类</text>
			</view>
			<view class="bottom_tab">
				<span class="iconfont icon-paixu"></span><text>排序</text>
			</view>
			<view class="bottom_tab">
				<span class="iconfont icon-xinjian"></span><text>新建商品</text>
			</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		onReady() {
			
			let that = this
			uni.getSystemInfo({
				success: function(res) {
					console.log(res)
					that.tabHeight = res.windowHeight - that.$store.state.kongHeight
				}
			})
		},
		components:{
			navbar
		},
		data(){
			return{
				tabHeight:'',
				classifyList:['套餐','水果','饮料'],
				indexs:0
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
		background: #F5F5F5;
	}
	.big_view{
		border-top: 4upx solid #F5F5F5;
		display: flex;
	}
	.scrollY{
		width: 23%;
		border-right: 4upx solid #F5F5F5;
	}
	.scrollX{
		width: 77%;
	}
	.scroll1{
		font-size: 30upx;
		height: 90upx;
		line-height: 90upx;
		width: 100%;
		text-align: center;
		color: #333333;
		background: #FFFFFF;
		border-bottom: 4upx solid #F5F5F5;
	}
	.scroll2{
		background: #FFBA59;
		color: #FFFFFF;
	}
	.scroll3{
		height: 320upx;
		background: #FFFFFF;
		border-bottom: 10upx solid #F5F5F5;
	}
	.bottom_view{
		position: fixed;
		bottom: 0;
		height: 88upx;
		width: 100%;
		
	}
</style>
