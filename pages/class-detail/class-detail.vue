<template>
	<view class="detail-page">
		<!-- 课程内容 -->
		<view class="class-content">
			<image src="http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACDztcHsBSiGoraPATDuBTj8AkBl.jpg" mode="widthFix"></image>
			<view class="title-box">
				<view class="title">【强化训练】诗歌典型题梳理</view>
				<button open-type="share" plain class="share"><u-icon @click="handleShare" size="46" color="#999999" name="zhuanfa"></u-icon></button>
			</view>
			<view class="summary">小班教学更能保证学习效果，高中班16人/班，其他班次20人/班</view>
			<view class="price">
				<text>￥2700.00</text>
				<text>已预约：12</text>
				<text>剩余：98</text>
			</view>
		</view>
		<!-- 课程详情 -->
		<view class="server__detail">
			<view class="server__detail-title"><u-section title="服务详情" font-size="26" :right="false"></u-section></view>
			<view class="server__detail-content">该课程由优秀教师围绕中考所有知识点进行授课，高频练习解题思路和解题技巧，提高学生综合运用知识点解题的能力，夯实基础</view>
			<image src="https://1.s91i.faiusr.com/4/AFsIkK06EAQYACDvlY-uBSjAgK-7BDDQBTiACg!800x800.png" mode="widthFix"></image>
		</view>
		<!-- 底部 -->
		<view class="footer-bar">
			<view class="phone" @click="handlePhoneCall">
				<u-icon size="48" name="phone"></u-icon>
				<view>电话</view>
			</view>

			<view class="btn"><u-button shape="circle" @click="goSettlement" type="warning">立即预约</u-button></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		goSettlement() {
			uni.navigateTo({
				url: '../settlement/settlement'
			});
		},
		// 拨打电话
		handlePhoneCall() {
			// #ifndef H5
			uni.makePhoneCall({
				phoneNumber: '15800021934'
			});
			// #endif
			// #ifdef H5
			uni.showActionSheet({
				itemList: ['15800021934'],
				success: function(res) {
					console.log(res.tapIndex);
				}
			});
			// #endif
		}
	},
	// 小程序分享
	onShareAppMessage(res) {
		return {
			title: '【强化训练】诗歌典型题梳理',
			path: '/pages/class-detail/class-detail'
		};
	}
};
</script>

<style lang="scss" scoped>
.detail-page {
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	// 课程内容
	.class-content {
		background-color: #ffffff;
		padding: 0 20rpx 20rpx;
		image {
			width: 100%;
			border-radius: 10rpx;
		}
		.title-box {
			padding: 10rpx 0;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.title {
				font-weight: 600;
				border: none;
				background-color: #ffffff;
			}
			.share {
				margin: 0;
				border: none;
			}
		}
		.summary {
			font-size: 24rpx;
			color: #999999;
			margin-bottom: 10rpx;
		}
		.price {
			display: flex;
			align-items: center;
			text {
				font-size: 24rpx;
				color: #999999;
				&:nth-child(1) {
					color: red;
					font-size: 36rpx;
					margin-right: 20rpx;
				}
				&:nth-child(2) {
					margin-right: 20rpx;
				}
			}
		}
	}
	// 服务详情
	.server__detail {
		padding: 10rpx;
		background-color: #ffffff;
		margin-top: 20rpx;
		padding-bottom: 120rpx;
		&-title {
			padding: 20rpx 0;
		}
		&-content {
			padding: 10rpx 0;
			border-top: 1rpx solid #eeeeee;
			color: #999999;
		}
		image{
			width: 100%;
		}
	}
	// 底部
	.footer-bar {
		position: fixed;
		height: 120rpx;
		background-color: #ffffff;
		left: 0;
		right: 0;
		bottom: 0;
		display: flex;
		box-sizing: border-box;
		align-items: center;
		padding: 0 20rpx;
		.phone {
			padding: 0 20rpx;
		}
		.btn {
			flex: 1;
			margin-left: 20rpx;
		}
	}
}
</style>
