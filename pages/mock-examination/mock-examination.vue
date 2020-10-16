<template>
	<view class="mock-examination-page">
		<view class="banner-img">
			<image src="http://932.s80i.faiusr.com/4/101/AFAIABAEGAAg1PT38gUo9I-lYjDuBTjoAg.png" mode="widthFix"></image>
		</view>
		<view class="content-list">
			<view class="item" v-for="item in 5" :key='item'>
				<view class="header">
					<view class="title">
						叉车司机N1模拟考试（学员版）
					</view>
					<view class="exam-btn">
						<u-icon size="30" name="file-text-fill"></u-icon>
						<text>考试</text>
					</view>
				</view>
				<view class="time">
					2020.07.20 16:09 - 2030.07.31 16:09
				</view>
				<view class="footer-bar">
					<view class="start-answer-btn" @click="goExamDetail">
						开始答题
					</view>
					<view class="answer-time">
						限时<text>60</text>分钟
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			goExamDetail(){
				uni.navigateTo({
					url: '../exam-detail/exam-detail'
				});
			}
		}
	}
</script>

<style lang="scss">
.mock-examination-page{
	background-color: #f4f4f4;
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	.banner-img{
		background-color: #FFFFFF;
		padding-bottom: 10rpx;
		image{
			width: 100%;
		}
	}
	.content-list{
		margin-top: 20rpx;
		background-color: #FFFFFF;
		padding: 20rpx;
		.item{
			box-shadow: rgba(0, 0, 0, 0.1) 0px 2px 15px 0px;
			margin-bottom: 30rpx;
			padding: 30rpx;
			border-radius: 10rpx;
			.header{
				display: flex;
				justify-content: space-between;
				align-items: center;
				.exam-btn{
					border: 1rpx solid #6576ef;
					padding: 5rpx 10rpx;
					border-radius: 6rpx;
					font-size: 26rpx;
					color: #6576ef;
					margin: 0;
				}
			}
			.time{
				margin-top: 20rpx;
				font-size: 24rpx;
				color: #999999;
			}
			.footer-bar{
				margin-top: 40rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.start-answer-btn{
					background-color: #6576ef;
					color: #FFFFFF;
					padding: 5rpx 30rpx;
					border-radius: 30rpx;
					font-size: 26rpx;
				}
				.answer-time{
					font-size: 24rpx;
					color: #999999;
					text{
						padding: 0 5rpx;
						color: #6576ef;
					}
				}
			}
		}
	}
}
</style>
