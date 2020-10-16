<template>
	<view class="recruit-plan-page">
		<tab-swiper :list='list' @changeTab='changeTab' :current='current' @changeSwiper='changeSwiper'>
			<template slot="body">
				<view class="recruit-class-wrapper">
					<view class="item" v-for="item in 5" :key="item" @click="goClassDetail">
						<image src="http://973946.s81i.faiusr.com/2/101/AFEI_rg7EAIYACD6tcHsBSis2aNvMO4FOPwCQGU.jpg" mode="widthFix"></image>
						<view class="title">
							小升初数学打牢基础
						</view>
						<view class="desc">
							该课程由优秀教师围绕中考所有知识点进行授课，高频练习解题思路和解题技巧，提高学生
						</view>
						<view class="price-wrap">
							<view class="info">
								<text>￥2500.00</text>
								<text>已预约: 2</text>
								<text>剩余: 98</text>
							</view>
							<view class="btn">
								<u-button shape='circle' size="mini" type="warning">立即预约</u-button>
							</view>
						</view>
					</view>
				</view>
			</template>
		</tab-swiper>
	</view>
</template>

<script>
import TabSwiper from '../../components/TabSwper.vue'
export default {
	components:{
		TabSwiper
	},
	data() {
		return {
			list: [
				{
					name: '全部'
				},
				{
					name: '热门课程'
				},
				{
					name: '小升初'
				},
				{
					name: '初中/中考'
				},
				{
					name: '高中/高考'
				}
			],
			current: 0
		};
	},
	methods: {
		changeTab(index) {
			this.current = index;
		},
		changeSwiper(index){
			this.current = index;
		},
		goClassDetail(){
			uni.navigateTo({
				url: '../class-detail/class-detail'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
	.recruit-plan-page{
		background-color: #f4f4f4;
		.recruit-class-wrapper{
			margin-top: 20rpx;
			background-color: $uni-bg-color-white;
			padding-bottom: 50rpx;
			.item{
				padding: 20rpx;
				border-bottom: 1rpx solid #EEEEEE;
				image{
					width: 100%;
					border-radius: 8rpx;
				}
				.title{
					padding: 10rpx 0;
					font-size: 30rpx;
					@include  text-ellipsis-1;
				    font-weight: 600;
				}
				.desc{
					font-size: 24rpx;
					color: $uni-text-color-grey;
					@include  text-ellipsis-1;
					margin-bottom: 20rpx;
				}
				.price-wrap{
					width: 100%;
					display: flex;
					justify-content: space-between;
					align-items: center;
					.info{
						text{
							font-size: 24rpx;
							color: $uni-text-color-grey;
							&:nth-child(1){
								font-size: 32rpx;
								color: rgb(255, 216, 60);
								margin-right: 20rpx;
							}
							&:nth-child(2){
								margin-right: 20rpx;
							}
						}
					}
				}
			}
		}
	}
</style>
