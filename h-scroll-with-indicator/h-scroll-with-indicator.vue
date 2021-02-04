<template>
	<view class="h-scroll-with-indacator">
		<scroll-view scroll-x="true" @scroll="scrollHandle"><slot></slot></scroll-view>
		<view class="indicator-wrap">
			<view class="indicator" :style="{ backgroundColor: background }">
				<view class="dot" :style="{ background: color, transform: `translate(${scrollIndacator})` }"></view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			scrollIndacator: '0%'
		};
	},
	props: {
		// 指示器颜色
		color: {
			default: '#2150ff'
		},
		// 指示器背景颜色
		background: {
			default: '#d1d8de'
		}
	},
	methods: {
		scrollHandle(info) {
			const { windowWidth } = uni.getSystemInfoSync();
			const viewWidth = info.detail.scrollWidth - windowWidth;
			let position = Number((info.detail.scrollLeft / viewWidth) * 100).toFixed(0);
			this.scrollIndacator = position + '%';
		}
	}
};
</script>

<style lang="scss" scoped>
.indicator-wrap {
	display: flex;
	justify-content: center;
	align-items: center;

	height: 40rpx;
	$indicatorWidth: 80rpx;
	$indicatorHeight: 8rpx;
	$indicatorRadius: 8rpx;
	.indicator {
		width: $indicatorWidth;
		height: $indicatorHeight;
		border-radius: $indicatorRadius;
		background: #d1d8de;
		.dot {
			width: $indicatorWidth/2;
			height: $indicatorHeight;
			border-radius: $indicatorRadius;
			background: #2150ff;
			will-change: transform;
		}
	}
}
</style>
