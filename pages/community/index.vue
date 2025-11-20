<template>
  <view class="page">
    <view class="list">
      <view class="post" v-for="(p,i) in posts" :key="i">
        <view class="header">
          <image class="avatar" src="/static/logo.png" mode="aspectFill"></image>
          <view class="meta">
            <text class="name">{{ p.name }}</text>
            <text class="time">{{ p.time }}</text>
          </view>
        </view>
        <view class="content">
          <text class="text">{{ p.text }}</text>
        </view>
        <view class="images">
          <image v-for="(img,j) in p.images" :key="j" class="img" :src="img" mode="aspectFill"></image>
        </view>
        <view class="actions">
          <view class="action">👍 {{ p.likes }}</view>
          <view class="action">💬 {{ p.comments }}</view>
        </view>
      </view>
    </view>
    <view class="fab">+</view>
  </view>
</template>

<script setup>
import { ref } from 'vue'
const posts = ref([
  { name: '张叔', time: '今天 09:20', text: '今天天气好，和老李去公园下棋', images: ['/static/logo.png'], likes: 12, comments: 3 },
  { name: '李阿姨', time: '昨天 17:05', text: '社区舞蹈队招人，一起来活动身体', images: ['/static/logo.png','/static/logo.png'], likes: 8, comments: 2 },
  { name: '王爷爷', time: '周二 08:12', text: '早起散步很舒服，大家注意保暖', images: ['/static/logo.png','/static/logo.png','/static/logo.png'], likes: 20, comments: 5 }
])
</script>

<style lang="scss">
.page { padding: 12px; }
.list { display:flex; flex-direction: column; gap: 12px; }
.post { background:#fff; border-radius: 12px; box-shadow: 0 6px 18px rgba(0,0,0,0.08); padding: 12px; }
.header { display:flex; align-items:center; gap: 10px; }
.avatar { width: 50px; height: 50px; border-radius: 25px; }
.meta { display:flex; flex-direction: column; }
.name { font-size: 18px; color:#333; }
.time { font-size: 16px; color:#888; }
.content { margin-top: 8px; }
.text { font-size: 18px; color:#333; line-height: 1.6; }
.images { margin-top: 8px; display:flex; flex-wrap: wrap; gap: 6px; }
.img { width: 32%; aspect-ratio: 1/1; border-radius: 8px; background:#f5f5f5; }
.actions { margin-top: 8px; display:flex; gap: 18px; color:#555; font-size: 16px; }
.fab { position: fixed; right: 18px; bottom: 70px; width: 56px; height: 56px; border-radius: 28px; background:#2E7D32; color:#fff; font-size: 28px; display:flex; align-items:center; justify-content:center; box-shadow: 0 10px 22px rgba(46,125,50,0.35); }
</style>