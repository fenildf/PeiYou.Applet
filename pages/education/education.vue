<template>
	<view class="education-page" style="margin-top: 0;">
		<!-- 导航icon -->
		<view class="navbar-box">
			<u-grid :col="4" :border="false">
				<u-grid-item bg-color="rgba(255,255,255,0)" v-for="(item, index) in navList" :key="index">
					<image :src="item.icon" mode="widthFix"></image>
					<view class="nav-text">{{ item.text }}</view>
				</u-grid-item>
			</u-grid>
		</view>
		<!-- 师资团队 -->
		<view class="teach-item-box">
			<u-section title="师资团队" color="#fff" line-color="rgb(255, 216, 60)" :right="false"></u-section>
			<view class="desc">我们的授课教师均具备5年以上教育经验，所教学生普遍有较大的成绩提升，并顺利进入理想学校</view>
			<view class="content">
				<u-row>
					<u-col span="6" v-for="(item, index) in teacherList" :key="index">
						<view class="item">
							<view class="teach-wrap">
								<view class="name">{{ item.name }}</view>
								<view class="teach-avatar"><image :src="item.avatar" mode="widthFix"></image></view>
							</view>
							<view class="teach-info">{{ item.desc }}</view>
						</view>
					</u-col>
				</u-row>
			</view>
		</view>
		<!-- 小班教育 -->
		<view class="small-class-box">
			<u-section title="小班教育" color="#fff" line-color="rgb(255, 216, 60)" :right="false"></u-section>
			<view class="content">
				<scroll-view scroll-x="true">
					<view class="class-list">
						<view class="class-item" v-for="item in 4" :key="item">
							<image src="http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACCN0sHsBSiQhvG5BzDHAjjaAUBl.jpg" mode="aspectFill"></image>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<!-- 招生办事处 -->
		<view class="office-box">
			<u-section title="招生办事处" color="#fff" line-color="rgb(255, 216, 60)" :right="false"></u-section>
			<view class="office-content">
				<view class="office-item" v-for="item in 3" :key="item" @click="goOfficeDetail">
					<view class="avatar"><u-avatar size="large" mode="square" src="http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg"></u-avatar></view>
					<view class="address-name">
						<view class="name">广州分校</view>
						<view class="address">广州市番禺区南村镇万博二路</view>
					</view>
					<view span="1"><u-icon name="phone-fill" color="rgb(255, 216, 60)" size="46"></u-icon></view>
				</view>
			</view>
		</view>
		<!-- 咨询问答 -->
		<view class="questions-answers-box">
			<u-section title="咨询问答" color="#fff" line-color="rgb(255, 216, 60)" @click="goNews"></u-section>
			<view class="questions-answers-content">
				<view class="item" v-for="item in 4" :key="item" @click="goNewsDetail">
					<view class="title">孩子考试太粗心？这六点助孩子告别粗心！</view>
					<view class="answers">孩子平时做题做错了，当父母问及他们原因时，听到的答案往往是“我太粗心了”。</view>
					<view class="time">2020-07-30</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			navList: [
				{
					icon: require('@/static/img/teacher_icon.png'),
					text: '师资雄厚'
				},
				{
					icon: require('@/static/img/teach-class_icon.png'),
					text: '课程丰富'
				},
				{
					icon: require('@/static/img/class_live-icon.png'),
					text: '信息化教育'
				},
				{
					icon: require('@/static/img/student-icon.png'),
					text: '学员见证'
				}
			],
			teacherList: [
				{
					name: 'Bella',
					avatar: require('@/static/img/teacher01.png'),
					desc: '英语专业和教育心理学专业双学位教学成果：八年级英语教学主管，从事中学英语教学十余年，桃李遍地。'
				},
				{
					name: 'Linda',
					avatar: require('@/static/img/teacher02.png'),
					desc: '语文教学主管，深谙深圳本土教材。在阅读作文的教学中，她以风趣幽默的教学，深入浅出的教学方法，激发学习兴趣和创作欲望。'
				},
				{
					name: 'Allen',
					avatar: require('@/static/img/teacher04.png'),
					desc: '主带五、六年级，教龄6年，教学经验丰富；深谙深圳小学教材及体系，专业基础扎实，曾参与教材编写，熟悉各个年级教学'
				},
				{
					name: 'Peter',
					avatar: require('@/static/img/teacher04.png'),
					desc: '毕业于西安交通大学，具有很强的数学功底，能因材施教，根据学生们各自的情况找到适合他们的教学方法。'
				}
			]
		};
	},
	methods: {
		goOfficeDetail(){
			uni.navigateTo({
				url: '../school/school'
			});
		},
		goNews(){
			uni.navigateTo({
				url: '../news/news'
			});
		},
		goNewsDetail(){
			uni.navigateTo({
				url: '../news-detail/news-detail'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.education-page /deep/ .u-grid-item {
	background-color: transparent;
}
.education-page {
	padding: 20rpx;
	background: url('https://s1.ax1x.com/2020/07/31/aMTDot.jpg') no-repeat center center/cover;
	// 导航
	.navbar-box {
		padding: 20rpx;
		image {
			width: 100rpx;
			height: 100rpx;
			border-radius: 50%;
		}
		.nav-text {
			color: #ffffff;
			margin-top: 20rpx;
		}
	}
	// 师资团队
	.teach-item-box {
		margin-top: 40rpx;
		.desc {
			margin: 30rpx 0 120rpx;
			color: #ffffff;
			font-size: 24rpx;
		}
		.content {
			.item {
				background-color: #ffffff;
				border-radius: 16rpx;
				margin: 5rpx;
				margin-bottom: 90rpx;
				height: 400rpx;
				.teach-wrap {
					position: relative;
					height: 120rpx;
					.name {
						position: absolute;
						text-align: right;
						left: 0;
						bottom: 0;
						width: 80%;
						background-color: #ffd83c;
						border-radius: 0 50rpx 50rpx 0;
						padding: 10rpx 20rpx;
					}
					.teach-avatar {
						position: absolute;
						bottom: -4px;
						left: 20rpx;
						width: 150rpx;
						image {
							width: 100%;
						}
					}
				}
				.teach-info {
					padding: 30rpx;
					font-size: 24rpx;
					line-height: 40rpx;
					overflow: hidden;
				}
			}
		}
	}
	// 小班教育
	.small-class-box {
		.content {
			margin-top: 20rpx;
			background-color: rgba(255, 255, 255, 0.2);
			border-radius: 10rpx;
			padding: 20rpx;
			padding-top: 30rpx;
			white-space: nowrap;
			overflow: hidden;
			.class-list {
				.class-item {
					&:nth-last-child(1){
						margin-right: 0;
					}
					width: 40%;
					display: inline-block;
					margin-right: 20rpx;
					image {
						width: 100%;
						height: 200rpx;
						border-radius: 6rpx;
					}
				}
			}
		}
	}
	,
	// 招生办事处
	.office-box {
		margin-top: 50rpx;
		.office-content {
			margin-top: 20rpx;
			background-color: $uni-bg-color-white;
			padding: 0 20rpx;
			border-radius: 10rpx;
			.office-item{
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 20rpx 0;
				border-bottom: 1rpx solid #EEEEEE;
				.address-name{
					margin-left: 20rpx;
					flex: 1;
				}
			}
			.name {
				margin-bottom: 20rpx;
			}
			.address {
				font-size: 24rpx;
				color: $uni-text-color-grey;
				margin-bottom: 10rpx;
			}
		}
	}
	// 咨询问答
	.questions-answers-box {
		margin-top: 50rpx;
		.questions-answers-content {
			margin-top: 20rpx;
			background-color: $uni-bg-color-white;
			border-radius: 10rpx;
			padding: 20rpx;
			.item {
				padding: 20rpx 10rpx;
				border-bottom: 1rpx solid #eeeeee;
				.answers {
					color: #9b9b9b;
					font-size: 24rpx;
					margin-top: 10rpx;
					@include text-ellipsis-1;
				}
				.time {
					color: #9b9b9b;
					font-size: 24rpx;
					margin-top: 20rpx;
				}
			}
		}
	}
}
</style>
