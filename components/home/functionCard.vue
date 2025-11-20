<template>
	<view class="page-container">
		<!-- 快捷入口卡片区域 -->
		<view class="quick-entry-section">
			<!-- 左侧大卡片 -->
			<view class="entry-card large-card" @click="handleCardClick('quick-consult')">
				<view class="card-header">
					<text class="title">极速问诊</text>
					<image class="arrow-icon" src="/static/image/home/functionCard/右箭头.png" mode="widthFix"></image>
				</view>
				<view class="card-desc">
					<text>智能分科室 </text>
					<text class="highlight">5分钟</text>
					<text> 回复</text>
				</view>
				<view class="tag-blue">
					<image class="flash-icon" src="/static/logo.png" mode="widthFix"></image>
					<text>急速接诊</text>
				</view>
				<image class="bg-icon chat-icon" src="/static/logo.png" mode="aspectFit"></image>
			</view>

			<!-- 右侧小卡片容器 -->
			<view class="right-column">
				<!-- 找医生卡片 -->
				<view class="entry-card small-card" @click="handleCardClick('find-doctor')">
					<view class="text-content">
						<view class="card-header">
							<text class="title">找医生</text>
							<image class="arrow-icon" src="/static/image/home/functionCard/右箭头.png" mode="widthFix"></image>
						</view>
						<view class="card-desc small">全国良医 在线接诊</view>
					</view>
					<image class="bg-icon doctor-icon" src="/static/logo.png" mode="aspectFit"></image>
				</view>

				<!-- 购药卡片 -->
				<view class="entry-card small-card" @click="handleCardClick('buy-medicine')">
					<view class="text-content">
						<view class="card-header">
							<text class="title">购药</text>
							<image class="arrow-icon" src="/static/image/home/functionCard/右箭头.png" mode="widthFix"></image>
						</view>
						<view class="card-desc small">正品保障 在线开方</view>
					</view>
					<image class="bg-icon pills-icon" src="/static/logo.png" mode="aspectFit"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 数据可以放在这里
			}
		},
		methods: {
			// 点击事件处理，方便后续增加跳转逻辑
			handleCardClick(type) {
				console.log('点击了卡片:', type);
				// uni.navigateTo({ url: '/pages/...' })
			}
		}
	}
</script>

<style lang="scss">
	// 页面背景色，与图片中类似
	.page-container {
		background-color: #f8f8f8;
		padding: 24rpx;
		box-sizing: border-box;
	}

	.quick-entry-section {
		display: flex;
		gap: 20rpx; // flex的间距属性，非常方便
	}

	// 通用卡片样式
	.entry-card {
		background-color: #fff;
		border-radius: 20rpx;
		padding: 24rpx;
		position: relative;
		overflow: hidden; // 防止背景图溢出
		box-shadow: 0 4rpx 20rpx rgba(0, 0, 0, 0.05); // 添加细微阴影，提升质感
		box-sizing: border-box;
		display: flex;

		// 点击效果
		&:active {
			background-color: #fafafa;
		}
	}

	.card-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		width: 100%;

		.title {
			font-size: 34rpx;
			font-weight: bold;
			color: #333;
		}
		
		.arrow-icon {
			width: 36rpx;
			height: 36rpx;
		}
	}

	.card-desc {
		font-size: 24rpx;
		color: #999;
		margin-top: 8rpx;
		
		&.small {
			margin-top: 4rpx;
		}

		.highlight {
			color: #007aff; // 主题蓝色
		}
	}

	// 背景大图标通用样式
	.bg-icon {
		position: absolute;
		z-index: 0;
		opacity: 0.8;
	}
	
	// 左侧大卡片
	.large-card {
		flex: 1;
		flex-direction: column;
		height: 300rpx;

		.tag-blue {
			display: inline-flex; 
			align-items: center;
			background-color: #e6f2ff;
			color: #007aff;
			padding: 6rpx 12rpx;
			border-radius: 15rpx;
			font-size: 22rpx;
			margin-top: 20rpx;
            width: 150rpx;
			
			.flash-icon {
				width: 20rpx;
				height: 20rpx;
				margin-right: 6rpx;
			}
		}

		.chat-icon {
			width: 120rpx;
			height: 120rpx;
			right: 24rpx;
			bottom: 24rpx;
		}
	}

	// 右侧小卡片
	.right-column {
		flex: 1;
		display: flex;
		flex-direction: column;
		gap: 20rpx;
	}

	.small-card {
		flex: 1; // 让两个小卡片平分右侧高度
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		height: 140rpx; // (300 + 20) / 2 - 10 = 140
		
		.text-content {
			display: flex;
			flex-direction: column;
			justify-content: center;
			position: relative;
			z-index: 1; // 保证文字在图标上层
		}
		
		// 覆盖一下内部header的宽度
		.card-header {
		    width: auto;
		}

		.doctor-icon {
			width: 110rpx;
			height: 110rpx;
			right: 10rpx;
			bottom: 0;
		}
		
		.pills-icon {
			width: 120rpx;
			height: 120rpx;
			right: 10rpx;
			bottom: -10rpx;
		}
	}

</style>
