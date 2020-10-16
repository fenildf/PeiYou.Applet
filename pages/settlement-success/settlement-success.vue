<template>
	<view class="settlement-success">
		<view class="complete">
			<view class="success-img"><image src="../../static/img/success-icon.png" mode="widthFix"></image></view>
			<view class="btn">
				<u-button @click="goAllOrder" class="review-order" type="success" ripple>查看订单</u-button>
				<u-button @click="goHome" class="back-home" type="info" ripple>返回首页</u-button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		goAllOrder() {
			uni.navigateTo({
				url: '../order/order'
			});
		},
		goHome() {
			uni.switchTab({
				url: '/pages/index/index'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.settlement-success {
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	display: flex;
	justify-content: center;
	align-items: center;
	.complete {
		width: 70%;
		margin-bottom: 50%;
		.btn {
			margin-top: 20rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.review-order {
				background-color: #72b54e;
			}
			.back-home {
				color: #72b54e;
			}
		}
		.success-img {
			width: 100%;
			text-align: center;
			image {
				width: 100%;
			}
		}
	}
}
</style>
