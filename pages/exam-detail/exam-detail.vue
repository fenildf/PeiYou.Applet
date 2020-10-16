<template>
	<view class="exam-detail-page">
		<view class="header">
			<view class="time">
				<u-icon size="34" name="clock"></u-icon>
				<u-count-down :timestamp="timestamp"></u-count-down>
			</view>
			<text class="line">|</text>
			<view class="answer-card" @click="switchAnswerCard">
				<u-icon size="34" :name="showAnswerCard ? 'edit-pen' : 'file-text'"></u-icon>
				<text>{{ showAnswerCard ? '返回答题' : '答题卡' }}</text>
			</view>
		</view>
		<!-- 答题内容 -->
		<view class="answer-content">
			<view class="header">
				<view class="title">
					{{ showAnswerCard ? '答题卡' : '选择题' }}
					<text v-if="!showAnswerCard">(1 分)</text>
				</view>
				<view class="answer-count" v-if="!showAnswerCard">
					{{ current + 1 }}
					<text>/{{ answerList.length }}</text>
				</view>
				<view class="answer-card-tips" v-else>
					<text></text>
					<text>已作答</text>
					<text></text>
					<text>未作答</text>
				</view>
			</view>
			<view class="answer-select-box" v-if="!showAnswerCard">
				<swiper class="swiper-box" :current="current" @change="handleSwiperChange">
					<swiper-item v-for="(item, index) in answerList" :key="index">
						<scroll-view style="height: 100%;" scroll-y="true">
							<view class="swiper-item">
								<view class="subject">《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。</view>
								<view class="option-box">
									<view class="option-item" :class="selectKey == selectAnswer ? 'active':''" @click="handleSelect(selectKey)" v-for="(selectValue,selectKey) in item.select" :key='selectKey'>{{selectKey}} {{selectValue}}</view>
								</view>
							</view>
						</scroll-view>
					</swiper-item>
				</swiper>
			</view>
			<!-- 答题卡内容 -->
			<view class="answer-card-content" v-if="showAnswerCard">
				<scroll-view style="height: 100%;" scroll-y="true">
					<view>
						<text class="active" v-for="(item, index) in answerList" :key="index" @click="handleAnswerSelect(index)">{{ index + 1 }}</text>
					</view>
				</scroll-view>
			</view>
		</view>
		<!-- 下一题，上一题 -->
		<view class="next-pre-box" v-if="!showAnswerCard">
			<view class="pre" @click="handlePre">上一题</view>
			<view class="next" @click="handleNext">下一题</view>
		</view>
		<!-- 提交答题卡 -->
		<view class="submit-answer-card" v-if="showAnswerCard"><view class="btn">提交并查看结果</view></view>
		<!-- 提示组件 -->
		<u-top-tips ref="uTips"></u-top-tips>
	</view>
</template>

<script>
export default {
	data() {
		return {
			timestamp: 3600,
			showAnswerCard: false,
			current: 0,
			selectAnswer:null, // 题目选项
			answerList: [
				{
					title: '《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。',
					select: {
						A: '交通部门',
						B: '质量技术监管部门',
						C: '劳动部门',
						D: '安全生产监督管理部门'
					}
				},
				{
					title: '《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。',
					select: {
						A: '交通部门',
						B: '质量技术监管部门',
						C: '劳动部门',
						D: '安全生产监督管理部门'
					}
				},
				{
					title: '《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。',
					select: {
						A: '交通部门',
						B: '质量技术监管部门',
						C: '劳动部门',
						D: '安全生产监督管理部门'
					}
				},
				{
					title: '《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。',
					select: {
						A: '交通部门',
						B: '质量技术监管部门',
						C: '劳动部门',
						D: '安全生产监督管理部门'
					}
				},
				{
					title: '《特种设备安全监察条例》所称的县以上地方特种设备安全监督管理部门在现行体制下是指（ ）。',
					select: {
						A: '交通部门',
						B: '质量技术监管部门',
						C: '劳动部门',
						D: '安全生产监督管理部门'
					}
				}
			]
		};
	},
	onUnload() {
		console.log('我已经接近死亡');
	},
	onBackPress(event) {
		console.log(event);
	},
	methods: {
		// 切换答题卡
		switchAnswerCard() {
			this.showAnswerCard = !this.showAnswerCard;
		},
		// 下一题
		handleNext() {
			this.current++;
			if (this.current >= this.answerList.length) {
				this.current = this.answerList.length - 1;
				this.$refs.uTips.show({
					title: '已经是最后一题了哦!',
					type: 'warning',
					duration: '2000' 
				});
			}
		},
		// 上一题
		handlePre() {
			this.current--;
			if (this.current < 0) {
				this.current = 0;
				this.$refs.uTips.show({
					title: '已经是第一题了哦!',
					type: 'warning',
					duration: '2000'
				});
			}
		},
		// 题目滑动改变时
		handleSwiperChange(e) {
			this.current = e.detail.current;
		},
		// 点击答题卡选项
		handleAnswerSelect(index) {
			this.current = index;
			this.showAnswerCard = false;
		},
		handleSelect(selectKey){
			this.selectAnswer = selectKey
		}
	}
};
</script>

<style lang="scss">
.exam-detail-page {
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	padding: 20rpx;
	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		background-color: #ffffff;
		padding: 30rpx;
		border-radius: 10rpx;
		.line {
			color: #999999;
		}
		.answer-card {
			text {
				margin-left: 10rpx;
			}
		}
	}
	.answer-content {
		margin-top: 20rpx;
		background-color: #ffffff;
		padding: 20rpx;
		box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 8px 0px;
		.header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			border-bottom: 2rpx solid #eeeeee;
			.title {
				border-left: 6rpx solid #6576ef;
				padding-left: 10rpx;
				text {
					margin-left: 10rpx;
					color: #999999;
				}
			}
			.answer-count {
				color: #6576ef;
				font-size: 38rpx;
				text {
					font-size: 28rpx;
					color: #999999;
				}
			}
		}
		.answer-select-box {
			height: 700rpx;
			.swiper-box {
				height: 100%;
				.swiper-item {
					padding: 20rpx;
					.subject {
						padding: 20rpx;
						margin-bottom: 20rpx;
					}
					.option-item {
						padding: 25rpx;
						border: 1rpx solid #dddddd;
						margin-bottom: 30rpx;
						border-radius: 10rpx;
						cursor: pointer;
					}
					.active {
						color: #6576ef;
						border-color: #6576ef;
					}
				}
			}
		}
	}
	// 上一题，下一题
	.next-pre-box {
		margin-top: 50rpx;
		padding: 20rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		view {
			cursor: pointer;
			padding: 10rpx 30rpx;
			border-radius: 10rpx;
			font-size: 24rpx;
			border: 1rpx solid #6576ef;
			margin: 0 40rpx;
		}
		.next {
			background-color: #6576ef;
			color: #ffffff;
		}
	}
	// 提交答题卡
	.submit-answer-card {
		position: fixed;
		left: 0;
		right: 0;
		bottom: 0;
		height: 100rpx;
		background-color: #ffffff;
		padding: 0 100rpx;
		display: flex;
		align-items: center;
		.btn {
			width: 100%;
			text-align: center;
			border-radius: 100rpx;
			background-color: #6576ef;
			color: #ffffff;
			padding: 15rpx;
		}
	}
	// 答题卡内容
	.answer-card-content {
		height: 70vh;
		padding: 20rpx;
		padding-bottom: 60rpx;
		view {
			display: flex;
			flex-wrap: wrap;
			text {
				margin: 10rpx;
				width: 70rpx;
				height: 70rpx;
				display: inline-block;
				text-align: center;
				line-height: 70rpx;
				border-radius: 50%;
				border: 1rpx solid #dddddd;
			}
			.active {
				color: #6576ef;
				border-color: #6576ef;
			}
		}
	}
	// 答题卡提示
	.answer-card-tips {
		display: flex;
		align-items: center;
		text {
			&:nth-child(1) {
				width: 20rpx;
				height: 20rpx;
				border-radius: 50%;
				display: inline-block;
				border: 1rpx solid #6576ef;
				margin-right: 10rpx;
			}
			&:nth-child(2) {
				margin-right: 40rpx;
			}
			&:nth-child(3) {
				width: 20rpx;
				height: 20rpx;
				border-radius: 50%;
				display: inline-block;
				border: 1rpx solid #dddddd;
				margin-right: 10rpx;
			}
		}
	}
}
</style>
