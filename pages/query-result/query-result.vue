<template>
	<view class="query-result">
		<view class="content">
			<u-cell-group>
				<u-cell-item title="姓名" value="阿宇" :arrow="false"></u-cell-item>
				<u-cell-item title="班级" value="二年2班" :arrow="false"></u-cell-item>
				<u-cell-item title="学号" value="0415" :arrow="false"></u-cell-item>
				<u-cell-item title="语文" value="90分" :arrow="false"></u-cell-item>
				<u-cell-item title="数学" value="85分" :arrow="false"></u-cell-item>
				<u-cell-item title="英语" value="95分" :arrow="false"></u-cell-item>
				<u-cell-item title="总分" value="270分" :arrow="false"></u-cell-item>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {}
};
</script>

<style lang="scss" scoped>
	.query-result{
		position: absolute;
		top: 0;
		right: 0;
		left: 0;
		bottom: 0;
		background-color: #f4f4f4;
		padding: 30rpx;
		.content{
			border-radius: 10rpx;
			overflow: hidden;
		}
	}
</style>
