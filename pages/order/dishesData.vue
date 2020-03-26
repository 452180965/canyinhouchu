<template>
	<view class="page">
		<navbar title="菜品数据" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="tab_view" :style="{top:tabHeight + 'px'}">
			<view class="tab" :class="indexs==index?'tab1':''" v-for="(item,index) in tabList" :key='index' @click="tabClick(index)">{{item}}</view>
		</view>
		<view class="tab_team_view" :style="{top:searchHeight + 'px'}">
			<view class="tab_team_box">
				<view class="tab_team" :class="teamIndex==index1?'tabTeam':''" v-for="(item,index1) in tabTeamList" :key="index1" @click="tabTeamClick(index1)">{{item}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		onReady() {
			this.tabHeight = this.$store.state.kongHeight
			this.searchHeight = this.$store.state.kongHeight + 40
		},
		components:{
			navbar
		},
		data(){
			return{
				tabHeight:'',
				searchHeight:'',
				tabList:['早餐','中餐','晚餐','宵夜'],
				tabTeamList:['今日订单','明日订单','后日订单'],
				indexs:0,
				teamIndex:0
			}
		},
		onLoad() {
			
		},
		methods:{
			tabClick(index){
				this.indexs = index
			},
			tabTeamClick(index){
				this.teamIndex = index
			},
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.tab_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 100%;
		position: fixed;
		left: 0;
		background: #FFFFFF;
	}
	.tab{
		width: 25%;
		height: 78upx;
		line-height: 78upx;
		text-align: center;
		font-size: 28upx;
		position: relative;
	}
	.tab1::after{
		position: absolute;
		bottom: 0;
		content: '';
		height: 4upx;
		width: 60upx;
		background: #FFBA59;
		left: 50%;
		margin-left: -30upx;
	}
	.tab_team_view{
		padding: 10upx 0;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		background: #FFFFFF;
		width: 100%;
		box-sizing: border-box;
		position: fixed;
		left: 0;
	}
	.tab_team_box{
		display: flex;
		flex-direction: row;
		align-items: center;
		background: #F5F5F5;
		border-radius: 34upx;
		overflow: hidden;
	}
	.tab_team{
		height: 50upx;
		width: 140upx;
		border-radius: 34upx;
		font-size: 24upx;
		line-height: 50upx;
		text-align: center;
	}
	.tabTeam{
		background: #FFBA59 !important;
		color: #FFFFFF;
	}
</style>
