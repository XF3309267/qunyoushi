<template>
	<view style="width: 100%;height: 100vh;">
		<u-tabs-swiper  
			class="navBar" 
			ref="uTabs"
			height="90"
			:list="list" 
			:current="current" 
			@change="tabsChange" 
			:is-scroll="false" 
			swiperWidth="750"
			:bold="false"
			bar-width="100"
			></u-tabs-swiper>
		<swiper class="page-container" style="height: calc(100vh - 5em);"  :current="swiperCurrent" @transition="transition" @animationfinish="animationfinish">
			<swiper-item class=""  style="height: calc(100vh-5em);">
				<view class="page-item">
					<view class="u-p-20">
						<u-search  
							placeholder="搜索已添加的关键词的通知,活动,接龙,话题" v-model="keyword" 
							:show-action="false"
							bg-color="#ececec"
							></u-search>
					</view>
					<CardItem></CardItem>
					<CardItem></CardItem>
					<view class="item-box">
						<view class="u-text-center u-p-10 bottom" style="height: 5em;">
							<view  style="height: 4em;line-height: 4em;">
								联系客服 |  更多产品 
							</view>
						</view>
					</view>
				</view>
			</swiper-item>

			<swiper-item class="">
				<view class="page-item">
					<CardItem></CardItem>
					<view class="item-box">
						<view class="u-text-center u-p-10 bottom" style="height: 5em;">
							<view style="height: 4em;line-height: 4em;">
								联系客服 |  更多产品 
							</view>
						</view>
					</view>
				</view>
			</swiper-item>
		 </swiper>
		 
		 	<view class="hide-Container" v-if="!userIsLogin">
				<view class="u-m-t-80">
					<view class="u-p-t-70 u-flex u-row-center">
						<view class="imgContainer" :style="[{backgroundColor:'#00aaff'}]" >
							<image src="https://cdn.jsdelivr.net/gh/XF3309267/imgs/img/%E9%80%9A%E7%9F%A5.png" mode="aspectFill"></image>	
						</view>
					</view>
					<view class="u-text-center u-p-20">
						登录后才能使用哦
					</view>
					<view class="btn-list u-flex u-row-center u-p-20">
						<u-button class="u-m-l-20 u-m-r-20" plain type="primary"> 了解群有事 </u-button>
						<u-button class="u-m-l-20 u-m-r-20" open-type="getUserInfo" type="success" @getuserinfo="btnGetInfo"> 微信登录 </u-button>
					</view>
				</view>
			</view>
			
	</view>

</template>

<script>
	import CardItem from '../../components/myComponents/CardItem/CardItem.vue'
	export default {
		data() {
			return {
				title: 'Hello',
				list: [{
									name: '发件箱'
								}, {
									name: '收件箱'
								}],
								// 因为内部的滑动机制限制，请将tabs组件和swiper组件的current用不同变量赋值
				current: 0, // tabs组件的current值，表示当前活动的tab选项
				swiperCurrent: 0,
				keyword:'',
				userInfo:'',
				userIsLogin: true,
			}
		},
		onLoad() {

		},
		mounted(){
			this.isPowerGetUser()
		},
		methods: {

				tabsChange(index) {
					this.swiperCurrent = index;
				},
				// swiper-item左右移动，通知tabs的滑块跟随移动
				transition(e) {
					let dx = e.detail.dx;
					this.$refs.uTabs.setDx(dx);
				},
				// 由于swiper的内部机制问题，快速切换swiper不会触发dx的连续变化，需要在结束时重置状态
				// swiper滑动结束，分别设置tabs和swiper的状态
				animationfinish(e) {
					let current = e.detail.current;
					this.$refs.uTabs.setFinishCurrent(current);
					this.swiperCurrent = current;
				 	this.current = current;
				},
				//  检测是否可以获取用户信息
				isPowerGetUser(){
					uni.getUserInfo({
							provider:'weixin',
							success:(res)=>{
								this.userInfo = res.userInfo
								this.getUserAfter(res.userInfo)
							},
							fail: () => {
								this. userIsLogin = false
							}
					})
				},
				// 通过按钮 获取用户信息
				btnGetInfo(res){
					this.userInfo = res.detail.rawData
					this.getUserAfter( res.detail.rawData)
				},
				// 获取本地存储的用户信息
				getUserFromLocal(){
					try {
					    const value = uni.getStorageSync('userInfo');
					    if (value) {
					       return value
					    }
					} catch (e) {
					    // error
					}
				},
				// 本地存储用户信息
				setUserToLocal(userInfo){
					uni.setStorage({
						key:'userInfo',
						data:userInfo,
						success:()=>{
							
						},
						fail:()=>{
							uni.showToast({
								title:'用户信息未保存',
								icon:'error'
							})
						}
					})
				},
				// getUserInfo agter to do 
				getUserAfter(userInfo){
					this.userIsLogin = true
					this.setUserToLocal(userInfo)
				}
		},
		components:{
			CardItem
		}
	}
</script>

<style scoped>
.navBar{
	height: 5em;
	letter-spacing: .1em;
}

.hide-Container{
	position: fixed;
	top: 0;
	left: 0;
	z-index: 10000;
	height: 100vh;
	width: 100%;
	background-color: #FFF;
}
.btn-list{
	
}
</style>
