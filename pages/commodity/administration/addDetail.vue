<template>
	<view class="page">
		<navbar title="新增菜品" :backcolorType='2' :showKongPanel="true" :whiteback="2"></navbar>
		<view class="img_view">
			<image class="food_img" src="/static/微信图片_20200318092008.jpg" mode="aspectFill" v-if="img"></image>
			<span class="iconfont icon-jiahao1"></span>
		</view>
		<view class="big_view">
			<view class="text_view">
				<text>菜品名称:</text>
				<input class="input"  type="text" placeholder="请输入菜品名称" @input="nameInput">
			</view>
			<view class="text_view">
				<text>菜品描述:</text>
				<input class="input" type="text" placeholder="请输入菜品描述" @input="introInput">
			</view>
			<view class="text_view" @click="classifyClick">
				<text>菜品类型:</text>
				<view class="text_right_view text_right_view1"><span class="iconfont icon-jiantou"></span><view class="class" v-if="smallType">{{classify[smallType - 1].name}}</view><span class="iconfont icon-zhiding" v-if="smallType&&bigType"></span><view class="class" v-if="bigType">{{classify[bigType - 1].name}}</view></view>
			</view>
			<view class="text_view">
				<text>菜品期限:</text>
				<view class="text_right_view">
					<checkbox-group>
						<label v-for="(item,index) in student" :key='index' @click='checkClick(item.id)'>
							<checkbox :value="item.id" :checked='item.checked'  style="transform:scale(0.7)" color="#FFBA59" /><text>{{item.name}}</text>
						</label>
					</checkbox-group>
				</view>
			</view>
			<view class="text_view">
				<text>菜品单价:</text>
				<input class="input" type="text" placeholder="请输入金额(元)" @input="cashInput" >
			</view>
			<view class="btn" @click="comfireClick">完成</view>
		</view>
	</view>
</template>

<script>
	import navbar from "@/components/navbar/navbar.vue"
	export default{
		components: {
			navbar
		},
		data(){
			return{
				boxType:false,
				student:[{
					name:'早餐',
					id: '1',
					checked:false
				},
				{
					name:'午餐',
					id: '2',
					checked:false
				},
				{
					name:'晚餐',
					id: '3',
					checked:false
				},
				{
					name:'夜宵',
					id: '4',
					checked:false
				},
				],
				allId: [],
				cashValue: '',
				introValue: '',
				nameValue: '',
				img:'',
				bigType:'',
				smallType:'',
				classify:[]
			}
		},
		onLoad() {
			
		},
		onShow() {
			console.log(this.classify)
			console.log(this.bigType)
			console.log(this.smallType)
		},
		methods:{
			classifyClick(){
				uni.navigateTo({
					url:"detailClassifyBig"
				})
			},
			comfireClick(){
				console.log(111,this.nameValue)
				console.log(222,this.introValue)
				console.log(333,this.cashValue)
			},
			nameInput(e){
				this.nameValue = e.detail.value
			},
			introInput(e){
				this.introValue = e.detail.value
			},
			cashInput(e){
				this.cashValue = e.detail.value
			},
			commentClick(){
				uni.navigateTo({
					url:'comment/comment'
				})
			},
			addGoodsClick(){
				this.boxType = true
			},
			checkClick(id){
				for(let i = 1;i<this.student.length;i++){
					if(this.student[i].id==id){
						this.student[i].checked = !this.student[i].checked
						console.log('111',this.student)
						break;
					}
				}
			},
		}
	}
</script>

<style>
	page{
		color: #333333;
	}
	.img_view{
		width: 100%;
		height: 480upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		background: #F5F5F5;
	}
	.food_img{
		width: 100%;
		height: 100%;
	}
	.icon-jiahao1{
		font-size: 80upx;
		color: #999999;
	}
	.big_view{
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding-top: 20upx;
	}
	.text_view{
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		justify-content: space-between;
		width: 65%;
		font-size: 30upx;
		padding: 20upx 0;
		border-bottom: 2upx solid #eeeeee;
	}
	.input{
		width: 60%;
		font-size: 30upx;
		text-align: right;
	}
	.text_right_view1{
		display: flex;
		flex-direction: row-reverse !important;
		
	}
	.text_right_view{
		width: 70%;
		display: flex;
		flex-direction: row;
		align-items: center;
		flex-wrap: wrap;
	}
	checkbox-group{
		font-size: 24upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		flex-wrap: wrap;
		width: 100%;
	}
	label{
		width: 50%;
		text-align: right;
	}
	.btn{
		width: 520upx;
		height: 78upx;
		font-size: 32upx;
		line-height: 78upx;
		background:linear-gradient(270deg,rgba(249,128,80,1) 1%,rgba(255,186,89,1) 100%);
		margin: 50upx auto 0;
		border-radius: 44upx;
		text-align: center;
		color: #FFFFFF;
	}
	.icon-zhiding{
		display: inline-block;
		transform: rotate(90deg);
	}
	.class{
		font-size: 24upx;
		color: #FFFFFF;
		background: #FFBA59;
		padding: 6upx 10upx;
		border-radius: 24upx;
		margin: 0 10upx;
		
	}
</style>
