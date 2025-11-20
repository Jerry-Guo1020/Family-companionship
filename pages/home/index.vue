<template>
	<view class="container">
		<view class="header-title">
			<text class="title-text">乐颐伴</text>
			<text class="title-desc">AI守护爸妈的健康日常。</text>
		</view>
		<view class="search-bar">
			<view class="search-box">
				<!-- <uni-icons type="search" size="24" color="#999"></uni-icons> -->
				<input class="placeholder" placeholder="搜索医生、科室、疾病"></input>
			</view>
			<!-- <uni-icons type="headphones" size="28" color="#333" class="icon-right"></uni-icons> -->
		</view>
		
		<scroll-view scroll-x class="tabs-scroll" :show-scrollbar="false">
			<view class="tabs">
				<text class="tab-item active">特邀专家</text>
				<text class="tab-item">耳鼻喉专家</text>
				<text class="tab-item">中医专家</text>
				<text class="tab-item">儿科专家</text>
			</view>
		</scroll-view>

		<FunctionCard />
			
			
			
	
	
	


		<!-- <view class="doctor-list">
			<view class="doctor-card" v-for="(doc, index) in doctors" :key="index">
				<view class="doc-header">
					<image :src="doc.avatar" class="avatar" mode="aspectFill"></image>
					<view class="doc-info">
						<view class="name-row">
							<text class="name">{{ doc.name }}</text>
							<text class="title">{{ doc.title }}</text>
						</view>
						<view class="hospital-row">
							<text class="tag-level">三甲</text>
							<text class="hospital">{{ doc.hospital }} | {{ doc.dept }}</text>
						</view>
						<view class="tags-row">
							<text class="feature-tag">从业{{doc.years}}年</text>
							<text class="feature-tag">回复快</text>
						</view>
					</view>
				</view>

				<view class="doc-skills">
					擅长：{{ doc.skills }}
				</view>

				<view class="doc-stats">
					<text class="star">★ {{ doc.score }}</text>
					<text class="count">接诊量 {{ doc.count }}</text>
					<text class="response">平均响应 {{ doc.time }}</text>
				</view>

				<view class="action-row">
					<view class="price-info">
						<view class="p-item"><uni-icons type="image" size="16" color="#007AFF"></uni-icons> 图文
							¥{{doc.priceText}}</view>
						<view class="p-item"><uni-icons type="videocam" size="16" color="#007AFF"></uni-icons> 视频
							¥{{doc.priceVideo}}</view>
					</view>
					<button class="btn-ask">去问诊</button>
				</view>
			</view>
		</view>

		<view class="science-section">
			<view class="section-header">
				<text class="section-title">每日小科普</text>
				<text class="more">查看更多 ></text>
			</view>
			<view class="video-card">
				<image src="/static/milk.jpg" mode="aspectFill" class="video-thumb"></image>
				<view class="play-btn">▶</view>
				<text class="video-title">晚上喝牛奶有助于睡眠？</text>
			</view>
		</view> -->
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue';
import FunctionCard from '../../components/home/functionCard.vue';
import NewsList from '../../components/home/newsList.vue';

	const doctors = ref([{
			name: '张三丰',
			title: '主任医师',
			hospital: '北京大学第一医院',
			dept: '心血管内科',
			years: 40,
			skills: '心血管疾病，心脏病，冠心病，高血压...',
			score: 5.00,
			count: '1.3万',
			time: '15分钟',
			priceText: 50,
			priceVideo: 80,
			avatar: '/static/doc1.png' // 请替换为实际图片路径
		},
		{
			name: '张五丰',
			title: '主治医师',
			hospital: '北京大学第十医院',
			dept: '心血管内科',
			years: 20,
			skills: '心血管疾病，心脏病，冠心病，高血压...',
			score: 4.96,
			count: '2.3千',
			time: '15分钟',
			priceText: 50,
			priceVideo: 80,
			avatar: '/static/doc2.png'
		}
	]);
</script>

<style lang="scss" scoped>
	.container {
		background-color: #f5f6fa;
		min-height: 100vh;
		padding-bottom: 40rpx;
	}

	.header-title {
		font-weight: 600;
		color: #333;
		padding: 40rpx 30rpx 20rpx 30rpx;
	}

	.title-text {
		font-size: 36rpx;
	}

	.title-desc {
		font-size: 20rpx;
	}


	/* 搜索栏 */
	.search-bar {
		display: flex;
		align-items: center;
		padding: 20rpx 30rpx;
		background: #fff;

		.search-box {
			flex: 1;
			background: #f0f0f0;
			border-radius: 40rpx;
			height: 80rpx;
			display: flex;
			align-items: center;
			padding: 0 30rpx;

			.placeholder {
				margin-left: 10rpx;
				color: #999;
				font-size: 30rpx;
			}
		}

		.icon-right {
			margin-left: 20rpx;
		}
	}

	/* Tabs */
	.tabs-scroll {
		background: #fff;
		white-space: nowrap;
		padding: 0 10rpx 20rpx;
	}

	.tabs {
		display: flex;
		padding: 0 20rpx;
	}

	.tab-item {
		font-size: 25rpx;
		color: #666;
		margin-right: 40rpx;
		padding-bottom: 10rpx;

		&.active {
			color: #333;
			font-weight: bold;
			font-size: 25rpx;
			border-bottom: 6rpx solid #ffd700;
		}
	}

	/* 医生卡片 */
	.doctor-card {
		margin: 20rpx 30rpx;
		background: #fff;
		border-radius: 20rpx;
		padding: 30rpx;
		box-shadow: 0 4rpx 16rpx rgba(0, 0, 0, 0.05);

		.doc-header {
			display: flex;

			.avatar {
				width: 100rpx;
				height: 100rpx;
				border-radius: 50%;
				margin-right: 20rpx;
				background: #eee;
			}

			.doc-info {
				flex: 1;

				.name-row {
					margin-bottom: 10rpx;

					.name {
						font-size: 36rpx;
						font-weight: bold;
						margin-right: 15rpx;
					}

					.title {
						font-size: 28rpx;
						color: #333;
						font-weight: bold;
					}
				}

				.hospital-row {
					display: flex;
					align-items: center;
					margin-bottom: 10rpx;

					.tag-level {
						background: #007AFF;
						color: #fff;
						font-size: 20rpx;
						padding: 2rpx 8rpx;
						border-radius: 6rpx;
						margin-right: 10rpx;
					}

					.hospital {
						font-size: 26rpx;
						color: #666;
					}
				}

				.tags-row {
					.feature-tag {
						background: #fff3cd;
						color: #856404;
						font-size: 22rpx;
						padding: 4rpx 10rpx;
						border-radius: 6rpx;
						margin-right: 10rpx;
					}
				}
			}
		}

		.doc-skills {
			font-size: 26rpx;
			color: #999;
			margin: 20rpx 0;
			white-space: nowrap;
			overflow: hidden;
			text-overflow: ellipsis;
		}

		.doc-stats {
			display: flex;
			align-items: center;
			font-size: 24rpx;
			color: #999;
			margin-bottom: 20rpx;

			.star {
				color: #ff9900;
				font-weight: bold;
				margin-right: 20rpx;
			}

			.count,
			.response {
				margin-right: 20rpx;
			}
		}

		.action-row {
			display: flex;
			justify-content: space-between;
			align-items: center;
			border-top: 1rpx solid #eee;
			padding-top: 20rpx;

			.price-info {
				display: flex;
				gap: 20rpx;

				.p-item {
					font-size: 26rpx;
					color: #007AFF;
					display: flex;
					align-items: center;
					gap: 6rpx;
				}
			}

			.btn-ask {
				margin: 0;
				background: #007AFF;
				color: #fff;
				font-size: 28rpx;
				border-radius: 40rpx;
				padding: 0 40rpx;
				height: 60rpx;
				line-height: 60rpx;
			}
		}
	}

	/* 科普 */
	.science-section {
		margin: 30rpx;

		.section-header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-bottom: 20rpx;
		}

		.section-title {
			font-size: 36rpx;
			font-weight: bold;
		}

		.more {
			font-size: 26rpx;
			color: #999;
		}

		.video-card {
			position: relative;
			height: 300rpx;
			border-radius: 20rpx;
			overflow: hidden;

			.video-thumb {
				width: 100%;
				height: 100%;
				background: #ddd;
			}

			.play-btn {
				position: absolute;
				left: 50%;
				top: 50%;
				transform: translate(-50%, -50%);
				background: rgba(0, 0, 0, 0.5);
				color: #fff;
				width: 80rpx;
				height: 80rpx;
				border-radius: 50%;
				text-align: center;
				line-height: 80rpx;
				font-size: 40rpx;
			}

			.video-title {
				position: absolute;
				bottom: 20rpx;
				left: 20rpx;
				color: #fff;
				font-size: 32rpx;
				font-weight: bold;
				text-shadow: 0 2rpx 4rpx rgba(0, 0, 0, 0.5);
			}
		}
	}
</style>