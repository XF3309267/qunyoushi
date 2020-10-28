<template>
	<view class="upload-container">
		<view class="list">
			<view v-for="item in listInfo" :key="item.id" class="item">
				<navigator :url="item.linkPath">
					<view
						class="imgContainer"
						:style="[{backgroundColor:item.bgColor}]"
					>
						<image :src="item.imgUrl" mode="aspectFill"></image>	
					</view>
				</navigator>
				
				<view class="subTitle">
					{{item.subTitle}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listInfo:[
					{id:0,imgUrl:'https://cdn.jsdelivr.net/gh/XF3309267/imgs/img/%E9%80%9A%E7%9F%A5.png',bgColor:'#ff557f',subTitle:'通知',linkPath:''},
					{id:1,imgUrl:'/static/upload/diaocha.png',bgColor:'#ff557f',subTitle:'文章',linkPath:''},
					{id:2,imgUrl:'/static/upload/start.png',bgColor:'#2979FF',subTitle:'活动',linkPath:''},
					{id:3,imgUrl:'/static/upload/qiandao.png',bgColor:'#47d6d6',subTitle:'签到',linkPath:''},
					{id:4,imgUrl:'/static/upload/toupiao.png',bgColor:'#ffaa7f',subTitle:'投票',linkPath:'/pages/vote/vote'},
					{id:5,imgUrl:'/static/upload/diaocha.png',bgColor:'#44cc64',subTitle:'调查问卷',linkPath:''},
					{id:6,imgUrl:'/static/upload/heart.png',bgColor:'#ff557f',subTitle:'送祝福',linkPath:''},
					{id:7,imgUrl:'/static/upload/qun.png',bgColor:'#7a69ff',subTitle:'群接龙',linkPath:''},
					{id:8,imgUrl:'/static/upload/huati.png',bgColor:'#44cc64',subTitle:'群活动',linkPath:''},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
.upload-container{
	min-height: 100vh;
	width: 100%;
	padding: 40rpx 10rpx;
	padding-top: 200rpx;
	display: flex;
	flex-flow: row nowrap;
	justify-content: center;
	align-items: flex-start;
}
.list{
	display: flex;
	justify-content: space-around;
	align-items: flex-start;
	flex-flow: row wrap;
	padding: 20rpx;
}
.item{
	padding: 20rpx 50rpx;
	text-align: center;
}

.subTitle{
	height: 2em;
	line-height: 2em;
}
</style>
