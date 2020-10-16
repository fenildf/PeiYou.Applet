<template>
	<view class="tabs-swiper-page">
		<view class="tabs-box"><u-tabs active-color="rgb(101, 118, 239)" :is-scroll="false" :list="list" :current="current" @change="changeTabs"></u-tabs></view>
		<swiper class="swiper-box" @change="changeSwiper" :current="current">
			<swiper-item v-for="(item, index) in list" :key="index">
				<view class="swiper-item">
					<scroll-view style="height: 100%;width: 100%;" scroll-y="true">
						<view class="content">
							<slot name="body" v-if="current == index"></slot>
						</view>
					</scroll-view>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
export default {
	props: {
		list: {
			type: Array
		},
		current: {
			type: Number,
			default: 0
		}
	},
	data() {
		return {};
	},
	methods: {
		// tab改变时
		changeTabs(index) {
			this.$emit('changeTab', index);
		},
		// swiper 改变时
		changeSwiper(e) {
			const index = e.detail.current;
			this.$emit('changeSwiper', index);
		}
	}
};
</script>

<style lang="scss" scoped>
.tabs-swiper-page {
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	bottom: 0;
	background-color: #f4f4f4;
	overflow: hidden;
	display: flex;
	flex-direction: column;
	.swiper-box {
		flex: 1;
		.swiper-item {
			height: 100%;
		}
	}
}
</style>
