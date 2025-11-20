<template>
  <view class="page">
    <view class="cards">
      <view class="card green">
        <text class="card-title">血压</text>
        <text class="card-value">{{ bp }}</text>
      </view>
      <view class="card blue">
        <text class="card-title">血糖</text>
        <text class="card-value">{{ sugar }}</text>
      </view>
      <view class="card orange">
        <text class="card-title">BMI</text>
        <text class="card-value">{{ bmi }}</text>
      </view>
    </view>

    <view class="chart">
      <text class="chart-text">最近7天血压趋势折线图</text>
      <text class="chart-sub">图表加载中...</text>
    </view>

    <view class="floating">
      <button class="record-btn">手动记录</button>
    </view>
  </view>
</template>

<script setup>
import { ref } from 'vue'
const bp = ref('120/80 mmHg')
const sugar = ref('5.6 mmol/L')
const bmi = ref('22.5 正常')
</script>

<style lang="scss">
.page {
  padding: 12px;
}

.cards {
  display: flex;
  gap: 12px;
}

.card {
  flex: 1;
  border-radius: 12px;
  padding: 12px;
  color: #fff;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.card-title {
  font-size: 18px;
}

.card-value {
  font-size: 20px;
  font-weight: 700;
}

.green {
  background: #43a047;
}

.blue {
  background: #42a5f5;
}

.orange {
  background: #fb8c00;
}

.chart {
  margin-top: 16px;
  height: 220px;
  border-radius: 12px;
  background: #fff;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.chart-text {
  font-size: 18px;
  color: #333;
}

.chart-sub {
  font-size: 16px;
  color: #777;
  margin-top: 6px;
}

.floating {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 20px;
  display: flex;
  justify-content: center;
  padding: 0 16px;
}

.record-btn {
  width: 100%;
  max-width: 520px;
  height: 48px;
  border-radius: 24px;
  background: #2E7D32;
  color: #fff;
  font-size: 18px;
  box-shadow: 0 8px 20px rgba(46, 125, 50, 0.35);
}
</style>