<template>
	<view class="container">
		<view class="u-flex u-row-around">
			<u-button type="primary" :plain="!leftBtnActive" @click="textVote"> 文字投票 </u-button>
			<u-button type="primary" :plain="leftBtnActive" @click="imgVote"> 图片投票 </u-button>
		</view>
		<view class="u-p-20" >
			<view class="">
				<input placeholder="投票标题" style="font-size: 40rpx;height: 80rpx;padding: 20rpx;" type="text" > </input>
				<u-line></u-line>
			</view>
			<view class="">
				<input placeholder="补充内容( 选填 )" style="font-size: 30rpx;height: 80rpx;padding: 20rpx;" type="text" > </input>
				<u-line></u-line>
			</view>
			<view class="">
				<u-row gutter="16">
					<u-col span="2">
						<view class="u-p-20">
							<u-icon name="minus-circle-fill" color="#ff0000" size="60"></u-icon>
						</view>
					</u-col>
					<u-col span="10">
						<input placeholder="选项" style="font-size: 30rpx;height: 80rpx;padding: 20rpx;" type="text" > </input>
						<u-line></u-line>
					</u-col>
				</u-row>
				<u-row gutter="16">
					<u-col span="2">
						<view class="u-p-20">
							<u-icon name="minus-circle-fill" color="#ff0000" size="60"></u-icon>
						</view>
					</u-col>
					<u-col span="10">
						<input placeholder="选项" style="font-size: 30rpx;height: 80rpx;padding: 20rpx;" type="text" > </input>
						<u-line></u-line>
					</u-col>
				</u-row>
				<u-row gutter="16">
					<u-col span="2">
						<view class="u-p-20">
							<u-icon name="plus" color="#00aaff" size="60"></u-icon>
						</view>
					</u-col>
					<u-col span="10">
						<view class="u-type-primary" style="font-size: 30rpx;height: 80rpx;padding: 20rpx;">
							添加选项
						</view>
						<u-line></u-line>
					</u-col>
				</u-row>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				leftBtnActive: true,
			}
		},
		methods: {
			textVote(){
				this.leftBtnActive = true
			}
		}
	}
</script>

<style scoped>
.container{
	padding: 30rpx 10rpx;
}
</style>
