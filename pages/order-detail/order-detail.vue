<template>
	<view class="order-detail">
		<view class="order-details-wrap">
			<view class="header">
				<u-icon name="order" size="60" color="green"></u-icon>
				<text>订单已经完成</text>
			</view>
			<view class="info-box">
				<view class="desc">
					<view class="order-img"><u-avatar size="large" mode="square" src="http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg"></u-avatar></view>
					<view class="order-info">
						<view class="title">小学升初中语文课程</view>
						<view class="desc">优秀教师结合学习热点、高频疑点，三审三教精心录制。课程内容充满趣味性，在学习同时</view>
						<view class="price">￥1288.00</view>
					</view>
				</view>
			</view>
			<!-- 预约信息 -->
			<view class="reserved-info">
				<view class="title">
					预约信息
				</view>
				<view class="buyer-info">
					<view class="name">
						预约人: 阿宇
					</view>
					<view class="phone">
						预约电话: 15800021934
					</view>
					<view class="message">
						买家留言: 255555555
					</view>
				</view>
			</view>
			<!-- 订单信息 -->
			<view class="order-info-box">
				<view class="title">
					订单信息
				</view>
				<view class="order-num">
					订单编号: 20200804
				</view>
				<view class="order-time">
					下单时间: 2020-08-04 22:30:13
				</view>
			</view>
			<!-- 订单按钮 -->
			<div class="btn-box">
				<view class="address">
					查看地址
				</view>
				<view class="call-us">
					联系我们
				</view>
			</div>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
.order-detail{
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	padding: 30rpx;
	.order-details-wrap{
		background-color: #FFFFFF;
		box-shadow: 0 0 5px 0 rgba(0,0,0,.05);
		.header{
			border-bottom: 1rpx dashed #e5e5e5;
			margin: 0 20rpx;
			padding: 40rpx 20rpx;
			display: flex;
			align-items: center;
			text{
				margin-left: 20rpx;
			}
			&::before{
				content: '';
				width: 28rpx;
				height: 28rpx;
				background-color: #f4f4f4;
				position: absolute;
				top: 155rpx;
				left: 16rpx;
				border-radius: 50%;
				display: block;
			}
			&::after{
				content: '';
				width: 28rpx;
				height: 28rpx;
				background-color: #f4f4f4;
				position: absolute;
				top: 155rpx;
				right: 16rpx;
				border-radius: 50%;
				display: block;
			}
		}
		.info-box{
			padding: 40rpx;
			border-bottom: 1rpx dashed #e5e5e5;
			.desc{
				display: flex;
				align-items: center;
				overflow: hidden;
				.order-info {
					margin-left: 20rpx;
					.title {
						font-weight: 600;
						@include text-ellipsis-1;
					}
					.desc {
						font-size: 24rpx;
						color: #999999;
						@include text-ellipsis-1;
					}
					.price {
						color: $uni-text-color-yellow;
						margin-top: 10rpx;
					}
				}
			}
		}
		/* 预留信息 */
		.reserved-info{
			padding: 40rpx;
			border-bottom: 1rpx dashed #e5e5e5;
			.title{
				font-weight: 600;
				margin-bottom: 20rpx;
			}
			.buyer-info{
				font-size: 24rpx;
				color: #999999;
				view{
					margin-bottom: 15rpx;
				}
			}
		}
		// 订单信息
		.order-info-box{
			padding: 40rpx;
			border-bottom: 1rpx dashed #e5e5e5;
			.title{
				font-weight: 600;
				margin-bottom: 20rpx;
			}
			.order-num,.order-time{
				font-size: 24rpx;
				color: #999999;
				margin-bottom: 15rpx;
			}
		}
		// 订单按钮
		.btn-box{
			cursor: pointer;
			display: flex;
			align-items: center;
			view{
				padding: 30rpx;
				text-align: center;
			}
			.address{
				width: 50%;
				border-right: 1rpx solid #e5e5e5;
			}
			.call-us{
				width: 50%;
			}
		}
	}
}
</style>
