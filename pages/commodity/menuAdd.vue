<template>
	<view class="page">
		<navbar title="菜单管理" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		
		<swiper class="swiper" :indicator-dots="false" :autoplay="false" :interval="3000" :duration="1000"
		 display-multiple-items='7'>
			<swiper-item v-for="(item,index) in week" :key="index">
				<view class="swiper-item" :class="item.keep?'active':''" @click="indexClick(index)">
					<view class="week">{{item.week}}</view>
					<view class="date">{{item.date}}</view>
				</view>
			</swiper-item>
		</swiper>
		<view id="line"></view>
		<view class="scroll" :style="{height:scrollHeight +'px'}">
			<scroll-view scroll-y="true" class="scrollY" :style="{height:scrollHeight +'px'}">
				<view v-for="(item,index1) in date" :key="index1" class="scroll1" :class="item.keep?'active':''" @click="indexClick1(index1)">{{item.week}}</view>
			</scroll-view>
			<scroll-view scroll-y="true" class="scrollX" :style="{height:scrollHeight +'px'}">
				<!-- <view class="titles"></view> -->
				<view class="foods_big_view">
					<view class="foods_view" v-for="(item,index) in foods" :key="index">
						<view class="foods_img_view">
							<image class="foods_img" src="/static/微信图片_20200318092008.jpg" mode="aspectFill"></image>
						</view>
						<view class="foods_name">油条 ￥10</view>
						<label @click="checkClick(index)">
							<checkbox style="transform: scale(0.7);" color="#FFBA59" /><text>上架</text>
						</label>
					</view>
				</view>
				
			</scroll-view>
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
			let that = this
			var query = uni.createSelectorQuery().in(this);
			query.select('#line').boundingClientRect(data => {
				console.log("1111", data);
				uni.getSystemInfo({
					success: function(res) {
						console.log(res)
						that.scrollHeight = res.windowHeight - data.top - 5
					}
				})
				// this.scrollHeight = this.$store.state.
			}).exec();
		},
		data(){
			return{
				scrollHeight:'',
				week: [{
					week: '周日',
					date: '8',
					keep:false
				}, {
					week: '周一',
					date: '9',
					keep:false
				}, {
					week: '周二',
					date: '10',
					keep:false
				}, {
					week: '周三',
					date: '11',
					keep:false
				}, {
					week: '周四',
					date: '12',
					keep:false
				}, {
					week: '周五',
					date: '13',
					keep:false
				}, {
					week: '周六',
					date: '14',
					keep:false
				}],
				date: [{
					week: '周日',
					date: '8',
					keep:false
				}, {
					week: '周一',
					date: '9',
					keep:false
				}, {
					week: '周二',
					date: '10',
					keep:false
				}, {
					week: '周三',
					date: '11',
					keep:false
				}, {
					week: '周四',
					date: '12',
					keep:false
				}, {
					week: '周五',
					date: '13',
					keep:false
				}, {
					week: '周六',
					date: '14',
					keep:false
				}],
				foods:[
					{
						name:"油条",
						keep:false
					},
					{
						name:"油条",
						keep:false
					},
					{
						name:"油条",
						keep:false
					},
					{
						name:"油条",
						keep:false
					},
					{
						name:"油条",
						keep:false
					},
				]
			}
		},
		onLoad() {
			
		},
		methods:{
			indexClick(index){
				this.week[index].keep = !this.week[index].keep
			},
			indexClick1(index){
				this.date[index].keep = !this.date[index].keep
			},
			checkClick(index){
				this.foods[index].keep = !this.foods[index].keep
				console.log(this.foods)
			},
		}
	}
</script>

<style>
	page{
		border: #F5F5F5;
	}
	/* 日期 */
	.swiper {
		width: 100%;
		border-top: 2upx solid #F5F5F5;
		height: 90upx;
	}
	.week {
		font-size: 28upx;
		color: #333;
		line-height: 1;
		opacity: 0.3;
	}

	.date {
		font-size: 30upx;
		line-height: 1;
		color: #333333;
		padding-top: 10upx;
	}

	.swiper-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 10upx 0;
	}
	.active{
		background: #FFBA59;
	}
	/* scroll */
	#line {
		width: 100%;
		height: 10upx;
		background: #F5F5F5;
	}
	
	.scroll {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		
	}
	
	.scrollY {
		width: calc(100% - 600upx);
	}
	
	.scroll1 {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 12upx 0;
		font-size: 26upx;
		height: 68upx;
		line-height: 68upx;
		border-bottom: 4upx solid #F5F5F5;
	}
	
	.scroll1_img_view {
		font-size: 0;
	}
	
	.scroll1_img {
		width: 88upx;
		height: 88upx;
		border-radius: 50%;
	}
	
	.scroll1 text {
		font-size: 24upx;
		line-height: 1;
		padding-top: 16upx;
	}
	
	.scrollX {
		width: 600upx;
		background: #F5F5F5;
	}
	/* foods */
	.foods_big_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		flex-wrap: wrap;
	}
	.foods_view{
		width: 200upx;
		display: flex;
		flex-direction: column;
		align-items: center;
		font-size: 28upx;
		color: #333333;
	}
	.foods_img_view{
		font-size: 0;
	}
	.foods_img{
		width: 180upx;
		height: 180upx;
	}
</style>
