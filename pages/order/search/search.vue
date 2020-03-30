<template>
	<view class="page">
		<navbar title="搜索" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="search_view" :style="{top:searchHeight + 'px'}">
			<view class="search">
				<span class='iconfont icon-sousuo'></span>
				<input class="search_input" type="text" :value="searchValue" placeholder-class="placeholder" placeholder="请输入学号或订单号" />
			</view>
			<view class="search_btn">查询</view>
		</view>
		<view class="tab_view" :style='{top:heights +"px"}'>
			<view class="tab_box">
				<view class="tab" :class="{active:type==0}" @click="tabClick(0)">全部<view>(100)</view>
				</view>
				<view class="tab" :class="{active:type==1}" @click="tabClick(1)"><span class='iconfont icon-good' :class='{active:type==1}'></span>
					<view>(50)</view>
				</view>
				<view class="tab" :class="{active:type==2}" @click="tabClick(2)"><span class='iconfont icon-good icon-good1' :class='{active:type==2}'></span>
					<view>(50)</view>
				</view>
			</view>
		</view>
		<view class="kongHeights"></view>
		<view class="table_view">
			<view class="table_left_view">
				<view class="table">日期</view>
				<view class="table" v-for="(item,index) in table" :key="index">{{item.id}}</view>
			</view>
			<view class="table_center_view">
				<view class="table">订单号</view>
				<view class="table" v-for="(item,index1) in table" :key="index1">{{item.name}}</view>
			</view>
			<view class="table_center_view1">
				<view class="table">状态</view>
				<view class="table" v-for="(item,index1) in table" :key="index1">{{item.type}}</view>
			</view>
			<view class="table_right_view">
				<view class="table"></view>
				<view class="table" @click="detailClick(item.name)" v-for="(item,index2) in table" :key="index2">详情</view>
			</view>
		</view>
		<view class="blackBG_view" v-if="blackType">
			<view class="blackBG"></view>
			<view class="black">
				<text class="text1">订单详情</text>
				<text>学号: 123456</text>
				<text>订单号: 1234567895</text>
				<text>下单时间: 2020-03-03 14:02</text>
				<text>预定时间: 2020-05-08 午餐</text>
				<text>订单状态: 已完成</text>
				<text>菜品: A套餐梅菜扣肉饭</text>
				<text>支付金额: 10</text>
				<view class="btn">退单处理</view>
				<span class="iconfont icon-jiahao" @click="closeClick"></span>
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
		onReady() {
			this.searchHeight = this.$store.state.kongHeight
			this.heights = this.$store.state.kongHeight + 44
		},
		data() {
			return {
				type: 0,
				blackType:false,
				heights: '',
				table: [{
						id: '2020-03-01',
						name: '4544589654',
						type: '3'
					},
					{
						id: '2020-03-01',
						name: '4544589654',
						type: '3'
					},
					{
						id: '2020-03-01',
						name: '4544589654',
						type: '3'
					}
				],
			}
		},
		onLoad(options) {
			if (options.value != '') {
				this.searchValue = options.value

			}
		},
		methods: {
			detailClick(id){
				this.blackType = true
			},
			closeClick(){
				this.blackType = false
			},
			tabClick(type) {
				this.type = type
			},
		}
	}
</script>

<style>
	page {
		background: #F5F5F5;
	}

	.search_view {
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
		z-index: 999;
	}

	.search {
		display: flex;
		align-items: center;
		border: 2upx solid #999999;
		border-radius: 34upx;
		height: 68upx;
		width: 500upx;
		padding: 0 20upx;
		box-sizing: border-box;
	}

	.icon-sousuo {
		color: #333333;
		padding-right: 10upx;
	}

	.search_input {
		color: #333333;
	}

	.placeholder {
		font-size: 32upx;
		color: #999999;
	}

	.search_btn {
		font-size: 32upx;
		color: #FFFFFF;
		width: 120upx;
		height: 68upx;
		border-radius: 34upx;
		background: linear-gradient(270deg, rgba(249, 128, 80, 1) 1%, rgba(255, 186, 89, 1) 100%);
		text-align: center;
		line-height: 68upx;
	}

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

	.tab_box {
		height: 48upx;
		border-radius: 64upx;
		background: #F5F5F5;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.tab {
		width: 200upx;
		font-size: 28upx;
		color: #333333;
		text-align: center;
		line-height: 48upx;
		height: 48upx;
		border-radius: 64upx;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.tab view {
		padding-left: 10upx;
	}

	.active {
		background: #FFBA59 !important;
		color: #FFFFFF !important;
	}

	.kongHeights {
		height: 156upx;
		width: 100%;
		opacity: 0;
	}

	.icon-good {
		color: #FFBA59;
		font-size: 32upx
	}

	.icon-good1 {
		font-size: 32upx;
		color: #999;
		display: inline-block;
		transform: rotateX(180deg);
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
		width: 35%;
		border-right: 1upx solid #999;
	}

	.table_center_view {
		width: 35%;
		border-right: 1upx solid #999;
	}
	.table_center_view1{
		width: 15%;
	}
	.table_right_view {
		width: 15%;
		border-left: 1upx solid #999999;
	}

	.table {
		width: 100%;
		height: 68upx;
		text-align: center;
		line-height: 68upx;
		font-size: 28upx;
		color: #333333;
	}

	.table:nth-of-type(2n-1) {
		background: #D6D6D6;
	}
	/* 浮窗 */
	.black{
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		width: 680upx;
		padding: 32upx;
		box-sizing: border-box;
		background: #FFFFFF;
		font-size: 28upx;
		color: #333333;
		position: fixed;
		top: 20%;
		left: calc(50% - 340upx);
		z-index: 99999999;
		border-radius: 34upx;
		line-height: 2;
	}
	.blackBG{
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 19999upx;
		z-index: 9999999;
		background: rgba(0,0,0,.5);
	}
	.text1{
		font-size: 36upx;
		width: 100%;
		text-align: center;
		padding-bottom: 10upx;
	}
	.btn{
		width: 140upx;
		height: 48upx;
		font-size: 28upx;
		background: #e5e5e5;
		text-align: center;
		line-height: 48upx;
		margin: 40upx auto 0;
		border-radius: 34upx;
		color: #666;
	}
	.icon-jiahao{
		transform: rotate(45deg);
		position: absolute;
		display: inline-block;
		color: #FFFFFF;
		left: ;
		font-size: 60upx;
		left: calc(50% - 62upx);
		bottom: -152upx;
		padding: 32upx;
		box-sizing: border-box;
	}
</style>
