<template>
	<view class="settlement-page">
		<view class="order__info">
			<view class="order__info-img"><image src="http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACD6tcHsBSis2aNvMO4FOPwCQGU.jpg" mode="widthFix"></image></view>
			<view class="order__info-detail">
				<view class="title">小升初语文基础课程</view>
				<view class="summary">优秀教师结合学习热点、高频疑点，三审三教精心录制。课程内容充满趣味性，在学习同时</view>
				<view class="price-wrap">
					<view class="price">￥2200.00</view>
					<view class="shop-icon">
						<u-icon color="rgb(101, 118, 239)" size="44" name="shopping-cart-fill"></u-icon>
						<text>到店支付</text>
					</view>
				</view>
			</view>
		</view>
		<!-- 数量 -->
		<view class="number-box">
			<text>数量</text>
			<u-number-box v-model="submitForm.num" @change="valChange"></u-number-box>
		</view>
		<!--买家信息 -->
		<view class="buyer__info">
			<view class="buyer__info-name"><u-field required v-model="submitForm.name" label="姓名" placeholder="请填写您的名字"></u-field></view>
			<view class="buyer__info-phone"><u-field v-model="submitForm.phone" label="手机号" required placeholder="请输入您的手机号码"></u-field></view>
			<view class="buyer__info-school"><u-field v-model="submitForm.school" label="就读学校" required placeholder="请填写学生就读学校"></u-field></view>
			<view class="enroll-school">
				<view class="title">报名校区</view>
				<view class="content">
					<u-radio-group v-model="submitForm.enrollSchoolValue" @change="radioGroupChange">
						<u-radio shape='circle' @change="radioChange" v-for="(item, index) in radioList" :key="index" :name="item.name" :disabled="item.disabled">{{ item.name }}</u-radio>
					</u-radio-group>
				</view>
			</view>
		</view>
		<!-- 留言 -->
		<view class="buyer-comments"><u-field type="textarea" required v-model="submitForm.comments" label="留言" placeholder="请输入您的留言信息"></u-field></view>
		<!-- 提交订单 -->
		<view class="footer-bar">
			<view class="price">￥2200.00</view>
			<view class="btn"><u-button shape="circle" @click="handleSubmit" type="warning">提交订单</u-button></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			submitForm: {
				num: 1,
				phone: '',
				name: '',
				school: '',
				comments: '',
				enrollSchoolValue:"雷州校区"
			},
			errorMessage: '请输入正确的手机号码！',
			radioList:[
				{
					name:'雷州校区',
					disabled: false
				},
				{
					name:'湛江校区',
					disabled: false
				},
				{
					name:'广州校区',
					disabled: false
				}
			]
		};
	},
	methods: {
		valChange() {},
		handleSubmit() {
			uni.navigateTo({
				url: '../settlement-success/settlement-success'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.settlement-page {
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	.order__info {
		display: flex;
		align-items: center;
		padding: 20rpx;
		background-color: #ffffff;
		border-top: 1rpx solid #eeeeee;
		&-img {
			padding: 10rpx;
			width: 30%;
			image {
				width: 100%;
			}
		}
		&-detail {
			padding: 20rpx;
			flex: 1;
			overflow: hidden;
			.summary {
				font-size: 24rpx;
				color: #999999;
				@include text-ellipsis-1;
			}
			.price-wrap {
				display: flex;
				justify-content: space-between;
				align-items: center;
				margin-top: 20rpx;
				.price {
					color: $uni-text-color-yellow;
					font-size: 32rpx;
				}
				.shop-icon {
					display: flex;
					align-items: center;
					text {
						margin-left: 10rpx;
					}
				}
			}
		}
	}
	// 数量
	.number-box {
		margin-top: 20rpx;
		background-color: #ffffff;
		padding: 30rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	// 卖家信息
	.buyer__info {
		margin-top: 20rpx;
		background-color: #ffffff;
	}
	// 留言
	.buyer-comments {
		margin-top: 20rpx;
		background-color: #ffffff;
	}
	// 选择报名校区
	.enroll-school {
		padding: 20rpx 10rpx;
		.title {
			&::before {
				content: '*';
				color: red;
				margin-right: 5rpx;
			}
		}
		.content{
			padding: 20rpx;
		}
	}
	// footer-bar
	.footer-bar {
		position: fixed;
		height: 120rpx;
		left: 0;
		bottom: 0;
		right: 0;
		background-color: #ffffff;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.price {
			padding: 0 20rpx;
			color: $uni-text-color-yellow;
			font-weight: 600;
			font-size: 32rpx;
		}
		.btn {
			flex: 1;
			padding: 0 20rpx;
		}
	}
}
</style>
