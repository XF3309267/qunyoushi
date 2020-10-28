<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	@import "uview-ui/index.scss";
	/*每个页面公共css */
	.title{
		font-weight: bold;
	}
.imgContainer{
	width: 4em;
	height: 4em;
	padding: 1em;
	border-radius: 50%;
}


.imgContainer image{
	width: 100%;
	height: 100%;
}
</style>
