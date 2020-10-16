<template>
	<view class="school-page">
		<!-- 背景 -->
		<view class="school-bg"></view>
		<!-- 机构信息 -->
		<view class="school-info-wrap">
			<view class="school-desc">
				<view class="title">皇家族培训基地</view>
				<view class="sub-title">广州总部</view>
				<view class="address">广州市天河区河陂南七巷1号(皇家族基地)</view>
				<view class="card">
					<view class="card-name">我的名片</view>
					<image src="../../static/img/my_home-icon-active.png" mode="widthFix"></image>
				</view>
				<view class="school-avatar">
					<u-avatar mode="square" size="large" src="http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACCBq8bsBSiUr5klMO4FOO4FQGU.jpg"></u-avatar>
				</view>
			</view>
			<!-- 联系我们 -->
			<view class="about-us">
				<u-cell-group>
					<u-cell-item title="15800021934" :arrow="false">
						<template #right-icon>
							<u-icon size="40" name="phone"></u-icon>
						</template>
					</u-cell-item>
					<u-cell-item title="969718197@qq.com" :arrow="false">
						<template #right-icon>
							<u-icon size="40" name="email"></u-icon>
						</template>
					</u-cell-item>
					<u-cell-item @click="handleLocal" title="广州市天河区河陂南七巷1号(皇家族基地)" :arrow="false">
						<template #right-icon>
							<u-icon size="40" name="map"></u-icon>
						</template>
					</u-cell-item>
					<u-cell-item title="Ayu0415" :arrow="false">
						<template #right-icon>
							<u-icon size="40" name="weixin-fill"></u-icon>
						</template>
					</u-cell-item>
				</u-cell-group>
			</view>
			<!-- 关于培优教育 -->
			<view class="about-peiyou">
				<u-card title="皇家族培训基地" :border="false">
					<view slot="body">该学校围绕中考所有知识点进行授课，高频练习解题思路和解题技巧，提高学生综合运用知识点解题的能力，夯实基础</view>
				</u-card>
			</view>
		</view>
		<!-- 底部信息 -->
		<view class="footer-bar">
			<view class="footer-icon">
				<view class="share">
					<u-icon size="40" name="share"></u-icon>
					<view class="text">分享</view>
				</view>
				<view class="home" @click="goHome">
					<u-icon size="40" name="home"></u-icon>
					<view class="text">首页</view>
				</view>
			</view>
			<view class="btn"><u-button shape="circle" type="warning">联系我们</u-button></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		goHome() {
			uni.switchTab({
				url: '../index/index'
			});
		},
		// 路线规划
		handleLocal() {
			// #ifdef MP-WEIXIN
			let plugin = requirePlugin('routePlan');
			let key = 'IR4BZ-K5UC6-5ZSSE-M2ZSQ-YUXO6-BPBZU'; //使用在腾讯位置服务申请的key
			let referer = '培优教育'; //调用插件的app的名称
			let endPoint = JSON.stringify({
				//终点
				name: '河陂南七巷1号(皇家族基地)',
				latitude: 23.207289,
				longitude: 113.372846
			});
			wx.navigateTo({
				url: 'plugin://routePlan/index?key=' + key + '&referer=' + referer + '&endPoint=' + endPoint
			});
			// #endif
		}
	}
};
</script>

<style lang="scss" scoped>
.school-page {
	background-color: #f4f4f4;
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	overflow: hidden;
	overflow-y: auto;
	.school-bg {
		position: absolute;
		background-color: rgb(101, 118, 239);
		height: 320rpx;
		width: 120%;
		border-radius: 0 0 45% 45%;
		left: -10%;
		overflow: hidden;
		cursor: pointer;
	}
	.school-info-wrap {
		position: absolute;
		z-index: 99;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		padding: 0 30rpx;
		.school-desc {
			position: relative;
			margin-top: 100rpx;
			border-radius: 10rpx;
			padding: 20rpx;
			background-color: #ffffff;
			box-shadow: 0 2px 20px 2px rgba(150, 150, 150, 0.2);
			.title {
				font-size: 36rpx;
				font-weight: bold;
			}
			.sub-title {
				margin-top: 20rpx;
				font-size: 40rpx;
				color: $uni-text-color-grey;
			}
			.address {
				font-size: 24rpx;
				margin-top: 5rpx;
				margin-bottom: 40rpx;
			}
			.card {
				border-top: 1rpx solid #eeeeee;
				padding: 20rpx;
				display: flex;
				justify-content: space-between;
				image {
					width: 40rpx;
					height: 40rpx;
				}
			}
			.school-avatar {
				position: absolute;
				top: 40rpx;
				right: 20rpx;
			}
		}
		// 联系我们
		.about-us {
			margin-top: 20rpx;
			background-color: #ffffff;
			overflow: hidden;
			box-shadow: 0 2px 20px 2px rgba(150, 150, 150, 0.2);
			border-radius: 10rpx;
		}
		// 关于培优
		.about-peiyou {
			margin-top: 20rpx;
			background-color: #ffffff;
			border-radius: 10rpx;
			overflow: hidden;
			margin-bottom: 140rpx;
		}
	}
	// 底部信息
	.footer-bar {
		position: fixed;
		right: 0;
		left: 0;
		bottom: 0;
		height: 120rpx;
		z-index: 999;
		background-color: #ffffff;
		display: flex;
		align-items: center;
		padding: 0 20rpx;
		.footer-icon {
			padding: 0 30rpx;
			width: 30%;
			display: flex;
			justify-content: space-between;
		}
		.btn {
			flex: 1;
		}
	}
}
</style>
