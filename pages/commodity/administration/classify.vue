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
		<block v-if="teamIndex==0">
			<view class="table_view table_view1" v-for="(item,index) in tableList" :key='index'>
				<view class="table_left_view">
					<view class="table">{{item.type}}</view>
				</view>
				<view class="table_center_view">
					<view class="table" v-if="item.keep==true">{{item.name}}</view>
					<view class="table" v-if="item.keep==false"><input class="input" type="text" @input="inputClick" /></view>
				</view>
				<view class="table_center_view1">
					<span class="iconfont icon-youjiantou iconTop" :class="index==0?'opacity':''" @click="topClick(index)"></span>
					<span class="iconfont icon-youjiantou iconDown" :class="index==tableList.length - 1?'opacity':''" @click="downClick(index)"></span>
				</view>
				<view class="table_right_view" @click="delClick(index)">
					<view class="table">删除</view>
				</view>
			</view>
		</block>
		<block v-if="teamIndex==1">
			<view class="table_view table_view1" v-for="(item,index) in tableList1" :key='index'>
				<view class="table_left_view">
					<view class="table">{{item.type}}</view>
				</view>
				<view class="table_center_view">
					<view class="table" v-if="item.keep==true">{{item.name}}</view>
					<view class="table" v-if="item.keep==false"><input class="input" type="text" @input="inputClick1" /></view>
				</view>
				<view class="table_center_view1">
					<span class="iconfont icon-youjiantou iconTop" :class="index==0?'opacity':''" @click="topClick(index)"></span>
					<span class="iconfont icon-youjiantou iconDown" :class="index==tableList1.length - 1?'opacity':''" @click="downClick(index)"></span>
				</view>
				<view class="table_right_view" @click="delClick(index)">
					<view class="table">删除</view>
				</view>
			</view>
		</block>
		<view class="table_btn_view">
			<view class="table_btn table_btn1" @click="addClick">添加</view>
			<view class="table_btn" @click="comfireClick">保存</view>
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
				nameValue:'',
				nameValue1:'',
				changeTpe: false,
				changeTpe1: false,
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
				],
				tableList1:[
					{
						name:'4',
						id:'4',
						type:'4',
						keep:true
					},
					{
						name:'5',
						id:'5',
						type:'5',
						keep:true
					},{
						name:'6',
						id:'6',
						type:'6',
						keep:true
					}
				],
			}
		},
		onLoad() {
			
		},
		methods:{
			inputClick(e){
				this.nameValue = e. detail.value
			},
			inputClick1(e){
				this.nameValue1 = e. detail.value
			},
			tabTeamClick(item,index){
				this.teamIndex = index
				this.title = item
			},
			topClick(index){
				let crr = []
				if(this.teamIndex==0){
					crr = this.tableList
				}else{
					crr = this.tableList1
				}
				// console.log(crr)
				let arr = crr.splice(index,1)
				// console.log(arr)
				crr.splice(index-1,0,arr[0])
				// console.log(crr)
				
				if(this.teamIndex==0){
					this.tableList = crr
				}else{
					this.tableList1 = crr
				}
			},
			downClick(index){
				let crr = []
				if(this.teamIndex==0){
					crr = this.tableList
				}else{
					crr = this.tableList1
				}
				// console.log(crr)
				let arr = crr.splice(index,1)
				// console.log(arr)
				crr.splice(index+1,0,arr[0])
				// console.log(crr)
				
				if(this.teamIndex==0){
					this.tableList = crr
				}else{
					this.tableList1 = crr
				}
			},
			delClick(index){
				if(this.teamIndex==0){
					this.tableList.splice(index,1)
				}else{
					this.tableList1.splice(index,1)
				}
			},
			addClick(){
				
				let crr = []
				if(this.teamIndex==0){
					if(this.changeTpe){
						uni.showToast({
							title:"请先完成前一个分类",
							icon:"none",
							duration:1500
						})
						return false
					}
					crr = this.tableList
					this.changeTpe = true
				}else{
					if(this.changeTpe1){
						uni.showToast({
							title:"请先完成前一个分类",
							icon:"none",
							duration:1500
						})
						return false
					}
					crr = this.tableList1
					this.changeTpe1 = true
				}
				let arr = {
					name:'',
					id: crr.length + 1,
					keep:false,
					type:crr.length + 1
				}
				crr.push(arr)
				
				if(this.teamIndex==0){
					this.tableList = crr
				}else{
					this.tableList1 = crr
				}
				
			},
			comfireClick(){
				let crr = []
				let arr = ''
				if(this.teamIndex==0){
					crr = this.tableList
					if(this.nameValue!=''){
						arr = this.nameValue
					}else{
						uni.showToast({
							title:"分类名不能为空",
							icon:"none",
							duration:1500
						})
					}
				}else{
					crr = this.tableList1
					if(this.nameValue1!=''){
						arr = this.nameValue1
					}else{
						uni.showToast({
							title:"分类名不能为空",
							icon:"none",
							duration:1500
						})
					}
				}
				for(let i =0;i<crr.length;i++){
					if(crr[i].keep ==false){
						crr[i].name = arr
						crr[i].keep = true
						
						break;
					}
				}
				if(this.teamIndex==0){
					this.tableList = crr
					this.changeTpe=false
				}
				else{
					this.tableList1 = crr
					this.changeTpe1 = false
				}
			},
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
	.table_view1:nth-of-type(2n){
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
	.input{
		height: 100%;
		width: 70%;
		font-size: 28upx;
		color: #333333;
		border: 1upx solid #999;
		margin: 0 auto;
	}
	/* 按钮 */
	.table_btn_view{
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 70%;
		margin: 120upx auto 0;
		justify-content: space-around;
	}
	.table_btn{
		width: 120upx;
		height: 58upx;
		font-size: 26upx;
		line-height: 58upx;
		text-align: center;
		border-radius: 34upx;
		color: #FFFFFF;
		background:linear-gradient(270deg,rgba(255,55,78,1) 1%,rgba(255,186,89,1) 100%);
	}
	.table_btn1{
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%) !important;
	}
</style>
