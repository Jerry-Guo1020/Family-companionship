<template>
	<view class="chat-container">
		<view class="nav-header">
			<uni-icons type="back" size="24"></uni-icons>
			<text class="title">极速问诊</text>
			<view class="right-icons">...</view>
		</view>

		<view class="steps-bar">
			<text class="step active">描述病情</text>
			<uni-icons type="arrowright" size="14" color="#ccc"></uni-icons>
			<text class="step">匹配医生</text>
			<uni-icons type="arrowright" size="14" color="#ccc"></uni-icons>
			<text class="step">开始咨询</text>
		</view>

		<scroll-view scroll-y class="chat-list" :scroll-into-view="lastId">

			<view class="guarantee-banner">
				<view class="g-title"><uni-icons type="checkbox-filled" color="#007AFF" size="16"></uni-icons> 服务保障
				</view>
				<view class="g-items">
					<text>● 三甲医生</text> <text>● 隐私保护</text> <text>● 多轮沟通</text> <text>● 超时退款</text>
				</view>
			</view>

			<view v-for="(msg, index) in messages" :key="index" :id="'msg-'+index" class="msg-item" :class="msg.type">
				<image v-if="msg.type === 'left'" src="/static/assistant.png" class="avatar"></image>

				<view class="bubble">
					<text>{{ msg.content }}</text>
				</view>

				<image v-if="msg.type === 'right'" src="/static/user.png" class="avatar"></image>
			</view>
		</scroll-view>

		<view class="bottom-area">

			<view v-if="status === 'tags'" class="quick-tags">
				<view class="tags-hint">您也可以点击以下标签，快速输入：</view>
				<view class="tags-wrap">
					<view class="tag" v-for="t in tags" :key="t" @click="sendTag(t)">{{t}}</view>
				</view>
				<view class="input-row">
					<input class="text-input" placeholder="请详细描述您的病情（至少2个字）" />
					<button class="btn-send">发送</button>
				</view>
			</view>

			<view v-if="status === 'upload'" class="upload-panel">
				<view class="panel-header">
					<text class="p-title">上传照片 (选填)</text>
					<text class="p-skip">跳过</text>
				</view>
				<view class="p-desc">请上传检查单/患处照片（最多9张）</view>
				<view class="upload-box">
					<view class="upload-btn">
						<uni-icons type="plusempty" size="40" color="#999"></uni-icons>
						<text>上传照片</text>
					</view>
				</view>
				<button class="btn-full" @click="status = 'form'">确定</button>
			</view>

			<view v-if="status === 'form'" class="form-panel">
				<view class="panel-header">
					<text class="back-btn" @click="status='upload'">
						< 返回</text>
							<text class="p-title">新建档案</text>
				</view>
				<view class="safe-tip">
					<uni-icons type="checkbox-filled" color="#007AFF" size="14"></uni-icons>
					为保护您的隐私，您的个人信息已经加密处理
				</view>

				<view class="form-item">
					<text class="label">姓名</text>
					<input placeholder="请输入患者姓名" class="input" />
				</view>

				<view class="form-item">
					<text class="label">性别</text>
					<view class="radio-group">
						<view class="radio checked"><uni-icons type="checkbox-filled" color="#007AFF"></uni-icons> 男
						</view>
						<view class="radio"><uni-icons type="circle" color="#ccc"></uni-icons> 女</view>
					</view>
				</view>

				<view class="form-item">
					<text class="label">生日</text>
					<text class="value-placeholder">请选择患者生日</text>
				</view>

				<view class="agreement">
					<uni-icons type="checkbox-filled" color="#007AFF" size="16"></uni-icons>
					我已阅读并知晓百灵医生的 <text class="link">《用户协议》</text> 和 <text class="link">《隐私政策》</text>
				</view>

				<button class="btn-full blue">发送</button>
			</view>

		</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue';

	const status = ref('tags'); // 'tags' | 'upload' | 'form'
	const tags = ['失眠', '咳嗽', '感冒', '肚子不舒服', '眼睛不舒服', '发烧', '头疼', '腹泻'];

	const messages = ref([{
			type: 'left',
			content: '您好，我是您的医生助手。'
		},
		{
			type: 'left',
			content: '请详细描述患者的病情（具体症状、患病时长、用药情况等）'
		},
		// 模拟用户发送后的状态
		// { type: 'right', content: '眼睛不舒服，已经一个星期了，滴了眼药水但是没有用' },
		// { type: 'left', content: '是否有检查单或患处照片？您上传的资料仅自己和医生可见' }
	]);

	const lastId = ref('');

	function sendTag(tag) {
		messages.value.push({
			type: 'right',
			content: tag
		});
		setTimeout(() => {
			messages.value.push({
				type: 'left',
				content: '是否有检查单或患处照片？您上传的资料仅自己和医生可见'
			});
			status.value = 'upload'; // 切换到底部上传状态
		}, 500);
	}
</script>

<style lang="scss" scoped>
	.chat-container {
		display: flex;
		flex-direction: column;
		height: 90vh;
		background: #f5f6fa;
	}

	/* 顶部 Header */
	.nav-header {
		height: 88rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 30rpx;
		background: #fff;
		font-size: 36rpx;
		font-weight: bold;
	}
	
	.steps-bar {
		display: flex;
		justify-content: space-around;
		align-items: center;
		background: #fff;
		padding: 20rpx 0;
		font-size: 28rpx;
		color: #999;
	}

	.steps-bar .active {
		color: #007AFF;
		font-weight: bold;
	}

	/* 聊天区 */
	.chat-list {
		flex: 1;
		padding: 20rpx;
		overflow: hidden;
	}

	.guarantee-banner {
		background: #fff;
		border-radius: 16rpx;
		padding: 20rpx;
		margin-bottom: 30rpx;
		width: 90%;

		.g-title {
			font-weight: bold;
			font-size: 30rpx;
			margin-bottom: 10rpx;
			display: flex;
			align-items: center;
			gap: 10rpx;
		}

		.g-items {
			display: flex;
			justify-content: space-between;
			color: #999;
			font-size: 24rpx;
		}
	}

	.msg-item {
		display: flex;
		margin-bottom: 30rpx;

		.avatar {
			width: 80rpx;
			height: 80rpx;
			border-radius: 50%;
			background: #ddd;
		}

		.bubble {
			max-width: 70%;
			padding: 20rpx;
			font-size: 32rpx;
			border-radius: 20rpx;
			position: relative;
		}

		&.left {
			flex-direction: row;

			.avatar {
				margin-right: 20rpx;
			}

			.bubble {
				background: #fff;
				color: #333;
			}
		}

		&.right {
			flex-direction: row-reverse;

			.avatar {
				margin-left: 20rpx;
			}

			.bubble {
				background: #d1e9ff;
				color: #333;
			}
		}
	}

	/* 底部区域通用 */
	.bottom-area {
		background: #fff;
		padding: 30rpx;
		border-radius: 30rpx 30rpx 0 0;
		box-shadow: 0 -4rpx 20rpx rgba(0, 0, 0, 0.05);
	}

	/* 状态1: 标签 */
	.quick-tags {
		.tags-hint {
			color: #666;
			font-size: 28rpx;
			margin-bottom: 20rpx;
		}

		.tags-wrap {
			display: flex;
			flex-wrap: wrap;
			gap: 20rpx;
			margin-bottom: 30rpx;
		}

		.tag {
			background: #e6f2ff;
			color: #007AFF;
			padding: 10rpx 30rpx;
			border-radius: 30rpx;
			font-size: 28rpx;
		}

		.input-row {
			display: flex;
			gap: 20rpx;

			.text-input {
				flex: 1;
				background: #f5f5f5;
				height: 80rpx;
				border-radius: 40rpx;
				padding: 0 30rpx;
			}

			.btn-send {
				width: 140rpx;
				height: 80rpx;
				line-height: 80rpx;
				background: #007AFF;
				color: #fff;
				border-radius: 40rpx;
				font-size: 30rpx;
			}
		}
	}

	/* 状态2: 上传 */
	.upload-panel {
		.panel-header {
			display: flex;
			justify-content: space-between;
			margin-bottom: 10rpx;
		}

		.p-title {
			font-size: 36rpx;
			font-weight: bold;
		}

		.p-desc {
			color: #999;
			font-size: 28rpx;
			margin-bottom: 30rpx;
		}

		.upload-box {
			display: flex;
			gap: 20rpx;
			margin-bottom: 40rpx;
		}

		.upload-btn {
			width: 160rpx;
			height: 160rpx;
			border: 2rpx dashed #ccc;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			color: #999;
			font-size: 24rpx;
			border-radius: 10rpx;
		}
	}

	/* 状态3: 表单 */
	.form-panel {
		.panel-header {
			display: flex;
			align-items: center;
			margin-bottom: 30rpx;
		}

		.back-btn {
			font-size: 28rpx;
			color: #666;
			margin-right: 20rpx;
		}

		.safe-tip {
			background: #f0f0f0;
			padding: 10rpx 20rpx;
			font-size: 24rpx;
			color: #666;
			margin-bottom: 30rpx;
			display: flex;
			align-items: center;
			gap: 10rpx;
			border-radius: 8rpx;
		}

		.form-item {
			display: flex;
			align-items: center;
			border-bottom: 1rpx solid #eee;
			padding: 30rpx 0;

			.label {
				width: 120rpx;
				font-size: 32rpx;
				font-weight: bold;
			}

			.input,
			.value-placeholder {
				flex: 1;
				font-size: 32rpx;
			}

			.value-placeholder {
				color: #999;
			}

			.radio-group {
				display: flex;
				gap: 40rpx;
			}

			.radio {
				display: flex;
				align-items: center;
				gap: 10rpx;
				font-size: 32rpx;
			}
		}

		.agreement {
			margin: 30rpx 0;
			font-size: 24rpx;
			color: #666;
			display: flex;
			align-items: center;
			gap: 10rpx;
		}

		.link {
			color: #007AFF;
		}
	}

	.btn-full {
		width: 100%;
		background: #007AFF;
		color: #fff;
		height: 90rpx;
		line-height: 90rpx;
		border-radius: 45rpx;
		font-size: 34rpx;
	}
</style>