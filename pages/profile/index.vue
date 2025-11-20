<template>
  <view class="page">
    <view class="header-card">
      <image class="avatar" src="/static/logo.png" mode="aspectFill"></image>
      <view class="info">
        <text class="name">王阿姨</text>
        <text class="age">72岁</text>
      </view>
    </view>

    <view class="menu">
      <view class="cell">
        <text class="label">我的亲情号</text>
        <text class="arrow">›</text>
      </view>
      <view class="cell">
        <text class="label">我的预约记录</text>
        <text class="arrow">›</text>
      </view>
      <view class="cell">
        <text class="label">我的活动</text>
        <text class="arrow">›</text>
      </view>
      <view class="cell">
        <text class="label">大字模式</text>
        <switch class="switch" :checked="largeFont" @change="onToggle" />
      </view>
      <view class="cell">
        <text class="label">设置</text>
        <text class="arrow">›</text>
      </view>
    </view>
  </view>
</template>

<script setup>
import { ref } from 'vue'
const largeFont = ref(false)
function onToggle(e) { largeFont.value = e.detail.value }
</script>

<style lang="scss">
.page { padding: 12px; }
.header-card { display:flex; align-items:center; gap: 12px; background:#fff; border-radius: 12px; padding: 12px; box-shadow: 0 6px 18px rgba(0,0,0,0.08); }
.avatar { width: 68px; height: 68px; border-radius: 34px; }
.info { display:flex; flex-direction: column; }
.name { font-size: 20px; color:#333; font-weight: 700; }
.age { font-size: 18px; color:#666; margin-top: 4px; }
.menu { margin-top: 16px; background:#fff; border-radius: 12px; box-shadow: 0 6px 18px rgba(0,0,0,0.08); overflow:hidden; }
.cell { display:flex; align-items:center; justify-content: space-between; padding: 14px 16px; border-bottom: 1px solid #f0f0f0; }
.cell:last-child { border-bottom: none; }
.label { font-size: 18px; color:#333; }
.arrow { font-size: 20px; color:#999; }
.switch { transform: scale(1.2); }
</style>