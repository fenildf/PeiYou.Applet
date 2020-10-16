<script>
export default {
	onLaunch: function() {
		// 登录授权
		// #ifdef MP-WEIXIN
		uni.login({
			provider: 'weixin',
			success: function(loginRes) {
				console.log(loginRes);
			}
		});
		// #endif
		console.log('App Launch');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style lang="scss">
@import 'uview-ui/index.scss';
</style>
