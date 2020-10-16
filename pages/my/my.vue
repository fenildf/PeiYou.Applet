<template>
	<view class="my-page">
		<!-- 背景 -->
		<view class="user-bg"></view>
		<!-- 用户容器 -->
		<view class="user-wrap">
			<!-- 用户信息 -->
			<view class="user-info">
				<button open-type="getUserInfo" @getuserinfo="handleGetuserinfo" class="login-avatar" type="default">
					<u-avatar size="large" :src="userInfo?userInfo.avatarUrl:'http://qz.faisys.com/image/head.png'"></u-avatar>
				</button>
				<view class="login-tips">{{userInfo?userInfo.nickName:'点击登录'}}</view>
			</view>
			<!-- cell 列表 -->
			<view class="cell-list-wrap">
				<!-- 所有订单 -->
				<view class="all-order">
					<u-cell-item @click="goAllOrder" title="所有订单"></u-cell-item>
					<u-grid :col="4" :border="false">
						<u-grid-item v-for="(item, index) in orderStatusList" :key="index" @click="goOrderStatus(index)">
							<u-badge count="9" :offset="[20, 25]"></u-badge>
							<u-icon color="rgb(101, 118, 239)" :name="item.icon" :size="46"></u-icon>
							<view class="text">{{ item.name }}</view>
						</u-grid-item>
					</u-grid>
				</view>
				<!-- 用户信息列表 -->
				<view class="list">
					<u-cell-group>
						<u-cell-item icon="setting-fill" title="最新信息"></u-cell-item>
						<u-cell-item icon="integral-fill" title="我的订阅"></u-cell-item>
						<u-cell-item icon="setting-fill" title="我的表单"></u-cell-item>
						<u-cell-item icon="integral-fill" title="我的打卡"></u-cell-item>
						<u-cell-item icon="setting-fill" title="我的优惠卷"></u-cell-item>
						<u-cell-item icon="integral-fill" title="我的报价"></u-cell-item>
					</u-cell-group>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			orderStatusList: [
				{
					name: '待支付',
					icon: 'order'
				},
				{
					name: '进行中',
					icon: 'order'
				},
				{
					name: '已完成',
					icon: 'order'
				},
				{
					name: '已取消',
					icon: 'order'
				}
			],
			userInfo: null
		};
	},
	created() {
		const value = uni.getStorageSync('userInfo');
		this.userInfo = JSON.parse(value);
		console.log(this.userInfo)
	},
	methods: {
		handleGetuserinfo(e) {
			const userInfo = e.detail.userInfo;
			uni.setStorageSync('userInfo', JSON.stringify(userInfo));
		},
		goAllOrder() {
			uni.navigateTo({
				url: '../order/order'
			});
		},
		goOrderStatus(index) {
			uni.navigateTo({
				url: `../order/order?status=${index}`
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.my-page {
	background-color: #f4f4f4;
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	overflow: hidden;
	overflow-y: auto;
	.user-bg {
		position: absolute;
		background-color: rgb(101, 118, 239);
		height: 320rpx;
		width: 120%;
		border-radius: 0 0 45% 45%;
		left: -10%;
		overflow: hidden;
		cursor: pointer;
	}
	.user-wrap {
		position: absolute;
		z-index: 99;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		.user-info {
			margin: auto;
			width: 140rpx;
			margin-top: 50rpx;
			.login-avatar {
				padding: 0;
				display: flex;
				justify-content: center;
				align-items: center;
				background-color: transparent;
				&::after {
					border: none;
				}
			}
			.login-tips {
				text-align: center;
				color: #ffffff;
				/* #ifdef MP-WEIXIN */
				margin-top: -20rpx;
				/* #endif */
			}
		}
		.cell-list-wrap {
			margin: 30rpx 60rpx;
			.all-order {
				background-color: #ffffff;
				border-radius: 10rpx;
				overflow: hidden;
				.text {
					margin-top: 10rpx;
					font-size: 24rpx;
				}
			}
			.list {
				margin-top: 20rpx;
				border-radius: 15rpx;
				overflow: hidden;
			}
		}
	}
}
</style>
