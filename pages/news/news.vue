<template>
	<view class="news-page">
		<tab-swiper :list="list" @changeTab="changeTab" :current="current" @changeSwiper="changeSwiper">
			<template slot="body">
				<view class="news-list">
					<view class="item" v-for="item in 6" :key="item" @click="goNewDetail">
						<u-row>
							<u-col span="10">
								<view class="title">如何培养数学思维能力？</view>
								<view class="desc">数学是中学科目，同为必学科目却比语文、英语要难以掌握，尤其对于文科生而言，数学学习是个坎。其实数</view>
								<view class="time">2020-07-30</view>
							</u-col>
							<u-col span="2"><u-avatar size="large" mode="square" src="http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg"></u-avatar></u-col>
						</u-row>
					</view>
				</view>
			</template>
		</tab-swiper>
	</view>
</template>

<script>
import TabSwiper from '../../components/TabSwper.vue';
export default {
	components: {
		TabSwiper
	},
	data() {
		return {
			list: [{ name: '全部' }, { name: '家庭教育' }, { name: '学习方法' }],
			current: 0
		};
	},
	methods: {
		changeTab(index) {
			this.current = index;
		},
		changeSwiper(index) {
			this.current = index;
		},
		goNewDetail(){
			console.log(546544)
			uni.navigateTo({
				url: '../news-detail/news-detail'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.news-page {
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	background-color: #f4f4f4;
	.news-list {
		margin-top: 20rpx;
		background-color: #ffffff;
		padding: 20rpx;
		.item {
			&:nth-last-child(1) {
				border: none;
			}
			border-bottom: 1rpx solid #eeeeee;
			padding: 20rpx;
			.title {
				font-weight: 700;
				@include text-ellipsis-1;
			}
			.desc {
				margin-top: 20rpx;
				font-size: 24rpx;
				color: $uni-text-color-grey;
				@include text-ellipsis-1;
			}
			.time {
				font-size: 24rpx;
				color: $uni-text-color-grey;
				margin-top: 15rpx;
			}
		}
	}
}
</style>
