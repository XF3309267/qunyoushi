<template>
	<view>
		<view class="u-flex u-row-center u-text-center" >
			<view class="u-p-t-60">
					<u-avatar class="avatar" :src="userInfo.avatarUrl" ></u-avatar>
					<view >
						{{userInfo===null?'匿名用户':userInfo.nickName}}
					</view>
			</view>
		</view>
		<view class="">
			<view class="" style="background-color: #e8e8e8;padding-bottom: 15rpx;">
				<view class="" style="background-color: #FFF;height: 3.5em;line-height: 3.5em;">
					<u-row gutter="16">
						<u-col span="11">
							<text class="u-p-15">群组</text>
						</u-col>
						<u-col span="1">
							<u-icon name="arrow-right" color="#cecece"></u-icon>
						</u-col>
					</u-row>
				</view>
			</view>
			<view class="" style="background-color: #e9e9e9;padding-bottom: 15rpx;">
				<view class="" style="background-color: #FFF;height: 3.5em;line-height: 3.5em;">
					<u-row gutter="16">
						<u-col span="11">
							<text >关于群里有事</text>
						</u-col>
						<u-col span="1">
							<u-icon name="arrow-right" color="#cecece"></u-icon>
						</u-col>
					</u-row>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userIsLogin:true,
				userInfo:null,
			}
		},
		mounted(){
			this.getUserInfo()
		},
		methods: {
				getUserInfo(){
					try {
							const value = uni.getStorageSync('userInfo');
							if (value) {
								this.userInfo = value
							}
					} catch (e) {
							// error
					}
				}
		}
	}
</script>

<style scoped>
	.avatar{
		width: 5em;
		height: 5em;
	}
</style>
