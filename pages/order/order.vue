<template>
	<view class="order-page">
		<tab-swiper :list="list" @changeTab="changeTab" :current="current" @changeSwiper="changeSwiper">
			<template slot="body">
				<u-card title="订单号:20174546" sub-title="进行中(到店付款)" :border="false">
					<view slot="body" class="card-body" @click="goOrderDetail">
						<view class="order-img"><u-avatar size="large" mode="square" src="http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg"></u-avatar></view>
						<view class="order-info">
							<view class="title">小学升初中语文课程</view>
							<view class="desc">优秀教师结合学习热点、高频疑点，三审三教精心录制。课程内容充满趣味性，在学习同时</view>
							<view class="price">￥1288.00</view>
						</view>
					</view>
					<view slot="foot"><u-button @click="handleOrderCancel" type="warning">取消预约</u-button></view>
				</u-card>
			</template>
		</tab-swiper>
		<!-- modal -->
		<u-modal
			:async-close="true"
			@confirm="handleOrderCancelconfirm"
			:show-title="false"
			show-cancel-button
			:mask-close-able="true"
			cancel-text="取消"
			v-model="showOrderCancel"
			content="您确定要取消该订单？"
		></u-modal>
	</view>
</template>

<script>
import TabSwiper from '../../components/TabSwper.vue';
export default {
	components: {
		TabSwiper
	},
	onLoad(option) {
		const index = Number(option.status) + 1
		if(option.status){
			this.current = index;
		}
	},
	data() {
		return {
			showOrderCancel: false,
			current: 0,
			list: [{ name: '全部' }, { name: '待支付' }, { name: '进行中' }, { name: '已完成' }, { name: '已取消' }]
		};
	},
	methods: {
		goOrderDetail(){
			uni.navigateTo({
				url: '../order-detail/order-detail'
			});
		},
		changeTab(index) {
			this.current = index;
		},
		changeSwiper(index) {
			this.current = index;
		},
		handleOrderCancel() {
			this.showOrderCancel = true;
		},
		handleOrderCancelconfirm() {
			setTimeout(() => {
				this.showOrderCancel = false;
				uni.showToast({
					icon:'success',
				    title: '取消成功',
				    duration: 1000
				});
			}, 1000);
		}
	}
};
</script>

<style lang="scss" scoped>
.order-page {
	.card-body {
		display: flex;
		align-items: center;
		.order-info {
			margin-left: 20rpx;
			overflow: hidden;
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
</style>
