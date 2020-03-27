<template>
	<view class="page">
		<navbar title="分类管理" :backcolorType='2' :showKongPanel="true" :whiteback='2'></navbar>
		<view class="tab_team_view" :style="{top:searchHeight + 'px'}">
			<view class="tab_team_box">
				<view class="tab_team" :class="teamIndex==index1?'tabTeam':''" v-for="(item,index1) in tabTeamList" :key="index1" @click="tabTeamClick(item,index1)">{{item}}</view>
			</view>
		</view>
		<view class="kongHeightView"></view>
		<view class="table_view">
			<view class="table_left_view">
				<view class="table">序号</view>
			</view>
			<view class="table_center_view">
				<view class="table">名称</view>
			</view>
			<view class="table_center_view1" style="justify-content: center;">
				<view class="table">排序</view>
			</view>
			<view class="table_right_view">
				<view class="table">操作</view>
			</view>
		</view>
		<view class="table_view table_view1" v-for="(item,index) in tableList" :key='index'>
			<view class="table_left_view">
				<view class="table">{{item.type}}</view>
			</view>
			<view class="table_center_view">
				<view class="table">{{item.name}}</view>
			</view>
			<view class="table_center_view1">
				<span class="iconfont icon-youjiantou iconTop" :class="index==0?'opacity':''" @click="topClick(index)"></span>
				<span class="iconfont icon-youjiantou iconDown" :class="index==tableList.length - 1?'opacity':''"></span>
			</view>
			<view class="table_right_view" @click="delClick(index)">
				<view class="table">删除</view>
			</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		onReady() {
			this.searchHeight = this.$store.state.kongHeight
		},
		components:{
			navbar
		},
		data(){
			return{
				searchHeight:'',
				tabTeamList:['大类','小类'],
				teamIndex:0,
				title:'大类',
				tableList:[
					{
						name:'1',
						id:'1',
						type:'1',
						keep:true
					},
					{
						name:'2',
						id:'2',
						type:'2',
						keep:true
					},{
						name:'3',
						id:'3',
						type:'3',
						keep:true
					}
				]
			}
		},
		onLoad() {
			
		},
		methods:{
			tabTeamClick(item,index){
				this.teamIndex = index
				this.title = item
			},
			topClick(index){
				let crr = this.tableList
				console.log(111,crr)
				let arr = this.tableList[index]
				let brr = this.tableList[index - 1]
				crr[index] = brr
				crr[index - 1] = arr
				this.tableList = crr
				console.log(222,crr)
			}
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
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
	.kongHeightView{
		height: 70upx;
		width: 100%;
	}
	.table_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: 710upx;
		margin: 30upx auto 0;
		font-size: 28upx;
		text-align: center;
		background: #c5c5c5;
		line-height: 58upx;
		border-top-left-radius: 14upx;
		border-top-right-radius: 14upx;
	}
	.table_view1{
		margin-top: 0 !important;
		border-radius: 0;
		background: #FFFFFF;
	}
	.table_view1:nth-last-of-type(2n){
		background: #C5C5C5 !important;
	}
	.table_left_view{
		width: 20%;
	}
	.table_center_view{
		width: 45%;
	}
	.table_center_view1{
		width: 15%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-around;
		
	}
	.table_right_view{
		width: 20%;
	}
	.iconTop{
		font-size: 32upx;
		color: #4CD964;
		transform: rotate(-90deg);
		padding: 0 20upx;
	}
	.iconDown{
		font-size: 32upx;
		color: #ff0000;
		transform: rotate(90deg);
		padding: 0 20upx;
		
	}
	.opacity{
		opacity: 0;
	}
</style>
