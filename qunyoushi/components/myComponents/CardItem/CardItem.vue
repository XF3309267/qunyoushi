<template>
	<view class="item-box">
		<view class="pro-item u-p-10" >
			<view class="u-p-8">
				<u-row gutter="16">
					<u-col span="9">
						<u-tag :text="cla" type="primary" bg-color="#FFF" shape="circle" />
						<text class="u-p-l-20 title"> 
							{{title}}
						</text>
					</u-col>
				</u-row>
			</view>
			<view class="u-p-8">
				<u-row gutter="16">
					<u-col span="9">
						<text class="u-type-default" > {{content}} </text>
					</u-col>
				</u-row>
			</view>
			<view class="u-p-8 u-font-12" >
				<u-row gutter="16">
					<u-col span="9">
						<text class="u-type-info " > 关键词：{{keyWord}} </text>
					</u-col>
	
				</u-row>
			</view>
			<view class="u-p-8 u-font-12" >
				<u-row gutter="16">
					<u-col span="9">
						<u-icon name="account" color="#d2d2d2" size="30"></u-icon>
						<text class="u-type-info u-p-l-10" > {{participants}} </text>
					</u-col>
					<u-col span="3">
						<view class="u-text-right">
							<u-icon name="clock" color="#d2d2d2" size="30"></u-icon>
							<text class="u-type-info u-p-l-10" > {{date}} </text>
						</view>
					
					</u-col>
				</u-row>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		name:'CardItem',
		props:{
			cla:{
				type: String,
				default:	'类目'
			},
			title:{
				type: String,
				default:	'标题'
			},
			content:{
				type: String,
				default:	'主要内容'
			},
			keyWord:{
				type: String,
				default:	'关键词'
			},
			participants:{
				type: String,
				default:	'发起者名称/参与人数'
			},
			date:{
				type: String,
				default:	'10.27'
			}
		}
	
	}
</script>

<style scoped>
.item-box{
	padding-bottom: 20rpx;
	background-color: #f3f3f3;
}
.pro-item,.bottom{
	background-color: #FFF;
}
</style>
