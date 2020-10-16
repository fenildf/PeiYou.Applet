<template>
	<view class="home">
		<!-- 首页轮播图 -->
		<view class="swiper-box"><u-swiper :list="swiperList" mode="round" height="500"></u-swiper></view>
		<!-- 导航 -->
		<view class="navber-box">
			<u-row>
				<u-col span="6" v-for="(item, index) in navList" :key="index" @click='goMockExam'>
					<view class="nav-item">
						<view class="left">
							<view>{{ item.title }}</view>
							<view>{{ item.subTitle }}</view>
						</view>
						<view class="right"><image :src="item.icon" mode="scaleToFill"></image></view>
					</view>
				</u-col>
			</u-row>
		</view>
		<!-- 教学优势 -->
		<view class="teach-superiority">
			<u-section title="教学优势" color="#fff" line-color="rgb(255, 216, 60)" :right="false"></u-section>
			<view class="content">
				<view class="item" v-for="(item, index) in teachSuperiorityList" :key="index">
					<view class="avatar"><image :src="item.imgUrl" mode="widthFix"></image></view>
					<view class="info-wrap">
						<view class="title">{{ item.title }}</view>
						<view class="info">{{ item.desc }}</view>
					</view>
				</view>
			</view>
		</view>
		<!-- 名师课堂 -->
		<view class="teaching-box">
			<u-section title="名师课堂" color="#fff" line-color="rgb(255, 216, 60)"></u-section>
			<view class="module-content">
				<scroll-view scroll-x="true">
					<view class="class-list">
						<view class="item" v-for="(item,index) in teachingList" :key="index" @click="goClassDetail">
							<image :src="item.imgUrl" mode="aspectFill"></image>
							<view class="title">{{item.title}}</view>
							<view class="sub-title">{{item.desc}}</view>
							<view class="price">
								<text>￥{{item.price}}</text>
								<text>已预约：{{item.reserved}}</text>
								<text>剩余：{{item.surplus}}</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<!-- 成绩查询 -->
		<view class="score-query">
			<view class="title">成绩查询</view>
			<view class="tips">可选择李四-三年2班-2号体验查询结果</view>
			<form>
				<view class="name">姓名</view>
				<u-input placeholder="请输入您的名字" v-model="form.name" border />
				<view class="classes">班级</view>
				<u-input placeholder="请输入选择您所在班级" v-model="form.class" border />
				<view class="student-number">学号</view>
				<u-input placeholder="请输入您的学号" v-model="form.studentNum" border />
				<view class="score-query-btn"><u-button @click="handleScoreQuery" type="warning">查询</u-button></view>
			</form>
		</view>
		<!-- 在线答题 -->
		<view class="on-line-answer">
			<view class="title">
				<u-divider color="#333">在线答题</u-divider>
			</view>
			<view class="content-list">
				<view class="item" v-for="item in 2" :key='item'>
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
		<!-- 家长好评 -->
		<view class="parent-appraise">
			<u-section title="家长评价" color="#fff" line-color="rgb(255, 216, 60)" :right="false"></u-section>
			<view class="content">
				<view class="item" v-for="item in 3" :key="item">
					<image src="https://wxt.sinaimg.cn/large/007XivJ0gy1g93mawj6coj30qn0qnabt.jpg" mode="widthFix"></image>
					<view class="info">非常感谢老师们专心用心的授课和点评，虽然跟优秀学生还有差距，但是近的成绩有了很大进步</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			showSeletClass: false,
			swiperList: [
				{
					image: 'http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACC0_8XsBSik6qOMAjDGBTj0A0Bl.jpg',
					title: '开学季'
				},
				{
					image: 'http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACC0_8XsBSjg9qr8BTDGBTj0A0Bl.jpg',
					title: '报名季'
				}
			],
			navList: [
				{
					icon: require('@/static/img/exam_icon.png'),
					title: '同步考试',
					subTitle: '直击开始'
				},
				{
					icon: require('@/static/img/guidance_icon.png'),
					title: '1对1辅导',
					subTitle: '个性化方案'
				},
				{
					icon: require('@/static/img/class_icon.png'),
					title: '培优班课',
					subTitle: '提升更有效'
				},
				{
					icon: require('@/static/img/teaching_icon.png'),
					title: '智慧教育',
					subTitle: '优质教学资源'
				}
			],
			teachSuperiorityList: [
				{
					title: '精英团队',
					desc: '211、985大学教育专业，历经层层考验筛选，专业技术过硬，家长认可。',
					imgUrl: 'http://973946.s81i.faiusr.com/4/101/AFEI_rg7EAQYACCcr8HsBSiLqY7FBDB4OHhAZQ.png'
				},
				{
					title: '辉煌成果',
					desc: '参加过培训的学生中，科率高达95%，其中有69%考上大学。',
					imgUrl: 'http://973946.s81i.faiusr.com/4/101/AFEI_rg7EAQYACCcr8HsBSj2-pqiBDB4OHhAZQ.png'
				},
				{
					title: '良好口碑',
					desc: '10年的沉淀打磨，自主研发了符合广东特色的教材与讲义，课内课外相结合。',
					imgUrl: 'http://973946.s81i.faiusr.com/4/101/AFEI_rg7EAQYACCcr8HsBSisjrXtBDB4OHhAZQ.png'
				}
			],
			teachingList:[
				{
					title:'【强化训练】小学精品班课课程',
					desc:"小班教学更能保证学习效果，高中班16人/初中班16人",
					imgUrl:'http://96644.s80i.faiusr.com/4/101/AFAIABAEGAAg2pzC6AUo_LKTgQQw7gU4-AI.png',
					price:'298.00',
					reserved:12,
					surplus:28
				},
				{
					title:'【强化训练】初中精品班课课程',
					desc:"语文、数学、英语、物理 等等小班教学更能保证学习效果，高中班16人/初中班16人",
					imgUrl:'http://96644.s80i.faiusr.com/4/101/AFAIABAEGAAg15zC6AUor6XbpgIw7gU4-AI.png',
					price:'498.00',
					reserved:25,
					surplus:8
				},
				{
					title:'【强化训练】高中精品班课课程',
					desc:"语文、数学、英语、理综 文综小班教学更能保证学习效果，高中班16人/初中班16人",
					imgUrl:'http://96644.s80i.faiusr.com/4/101/AFAIABAEGAAg15zC6AUo0OXjuQUw7gU4-AI.png',
					price:'688.00',
					reserved:20,
					surplus:10
				},
				{
					title:'【强化训练】iEAC青少英语能力课程',
					desc:"外教授课、国际课堂、托福加特小班教学更能保证学习效果，高中班16人/初中班16人",
					imgUrl:'http://96644.s80i.faiusr.com/4/101/AFAIABAEGAAgu7i18AUo98uDTjDuBTj8Ag.png',
					price:'598.00',
					reserved:12,
					surplus:28
				}
			],
			form: {
				name: '',
				class: '',
				studentNum: ''
			}
		};
	},
	onLoad() {},
	methods: {
		handleScoreQuery() {
			uni.navigateTo({
				url: '../query-result/query-result'
			});
		},
		goClassDetail() {
			uni.navigateTo({
				url: '../class-detail/class-detail'
			});
		},
		goMockExam(){
			uni.navigateTo({
				url: '../mock-examination/mock-examination'
			});
		},
		goExamDetail(){
			uni.navigateTo({
				url: '../exam-detail/exam-detail'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.home {
	background: url('https://s1.ax1x.com/2020/07/31/aMTDot.jpg') no-repeat center center/cover;
	.swiper-box {
		padding: 20rpx;
	}
	// 导航
	.navber-box {
		padding: 30rpx 40rpx;
		.nav-item {
			background-color: rgba(255, 255, 255, 0.2);
			border-radius: 16rpx;
			padding: 30rpx;
			margin-bottom: 20rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			color: #ffffff;
			.left {
				view {
					&:nth-child(1) {
						font-size: 26rpx;
					}
					&:nth-child(2) {
						font-size: 18rpx;
						color: rgba(255, 255, 255, 0.8);
						margin-top: 3rpx;
					}
				}
			}
			.right {
				width: 80rpx;
				height: 80rpx;
				image {
					width: 100%;
					height: 100%;
				}
			}
		}
	}

	// 教学优势
	.teach-superiority {
		padding: 20rpx;
		.content {
			margin-top: 20rpx;
			background-color: $uni-bg-color-white;
			padding: 30rpx 10rpx;
			border-radius: 10rpx;
			.item {
				&:nth-last-child(1) {
					margin-bottom: 0;
				}
				margin-bottom: 30rpx;
				display: flex;
				align-items: center;
				image {
					width: 140rpx;
					height: 140rpx;
				}
				.info-wrap {
					margin-left: 30rpx;
					.title {
						color: rgb(53, 53, 53);
						font-weight: bold;
						line-height: 40rpx;
						font-size: 30rpx;
					}
					.info {
						padding: 10rpx 0;
						font-size: 24rpx;
					}
				}
			}
		}
	}
	// 名师课堂
	.teaching-box {
		padding: 20rpx;
		.module-content {
			margin-top: 30rpx;
			background-color: #ffffff;
			border-radius: 10rpx;
			padding: 20rpx;
			white-space: nowrap;
			.class-list {
				display: flex;
				flex-wrap: nowrap;
			}
			.item {
				width: 60%;
				margin-right: 20rpx;
				image {
					width: 100%;
					height: 260rpx;
					border-radius: 10rpx;
				}
				.title {
					@include text-ellipsis-1;
				}
				.sub-title {
					@include text-ellipsis-1;
					color: $uni-color-subtitle;
					font-size: 24rpx;
					margin: 5rpx 0 10rpx;
				}
				.price {
					text {
						&:nth-child(1) {
							color: red;
							font-weight: 800;
							font-size: $uni-font-size-lg;
							margin-right: 10rpx;
						}
						&:nth-child(2) {
							font-size: $uni-font-size-sm;
							color: $uni-text-color-grey;
							margin-right: 10rpx;
						}
						&:nth-child(3) {
							font-size: $uni-font-size-sm;
							color: $uni-text-color-grey;
						}
					}
				}
			}
		}
	}
	// 在线答题
	.on-line-answer{
		margin: 20rpx;
		padding: 20rpx;
		border-radius: 10rpx;
		background-color: #FFFFFF;
		.title{
			padding: 20rpx;
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
	// 家长评价
	.parent-appraise {
		padding: 20rpx;
		.content {
			margin-top: 20rpx;
			.item {
				display: flex;
				align-items: center;
				color: #ffffff;
				font-size: 25rpx;
				padding: 30rpx;
				border-radius: 10rpx;
				background-color: rgba(255, 255, 255, 0.25);
				margin-bottom: 20rpx;
				image {
					width: 300rpx;
					height: 300rpx;
					border-radius: 50%;
					border: 2rpx solid #ffffff;
					margin-right: 30rpx;
				}
			}
		}
	}
	// 成绩查询
	.score-query {
		margin: 20rpx;
		padding: 40rpx;
		border-radius: 10rpx;
		background-color: $uni-bg-color-white;
		.title {
			font-size: 30rpx;
			color: #333;
			text-align: center;
			margin-bottom: 20rpx;
		}
		.tips {
			font-size: 24rpx;
			color: #999;
			text-align: center;
			margin-bottom: 40rpx;
		}
		form {
			.name,
			.classes,
			.student-number {
				margin: 20rpx 0;
				&::before {
					content: '*';
					color: red;
					vertical-align: middle;
					margin-right: 10rpx;
				}
			}
		}
		.score-query-btn {
			margin-top: 60rpx;
			font-size: 30rpx;
			color: #ffffff;
			border: none;
			cursor: pointer;
		}
	}
}
</style>
