<template>
  <view class="container">
    <view class="tab-bar">
      <view class="tab-item" :class="{active: activeTab === 'home'}" @click="changeTab('home')">
        <text>首页</text>
      </view>
      <view class="tab-item" :class="{active: activeTab === 'plan'}" @click="changeTab('plan')">
        <text>计划</text>
      </view>
      <view class="tab-item" :class="{active: activeTab === 'reward'}" @click="changeTab('reward')">
        <text>奖励</text>
      </view>
      <view class="tab-item" :class="{active: activeTab === 'setting'}" @click="changeTab('setting')">
        <text>设置</text>
      </view>
    </view>
    <view class="page-container">
      <keep-alive>
        <component :is="activeTab"></component>
      </keep-alive>
    </view>
  </view>
</template>

<script>
import home from '@/pages/home/index.vue'
import plan from '@/pages/plan/index.vue'
import reward from '@/pages/reward/index.vue'
import setting from '@/pages/setting/index.vue'

export default {
  data() {
    return {
      activeTab: 'home'
    }
  },
  components: {
    home,
    plan,
    reward,
    setting
  },
  methods: {
    changeTab(tab) {
      this.activeTab = tab
    }
  }
}
</script>

<style lang="scss">
.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.tab-bar {
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  box-shadow: 0 2px 10px 0 rgba(0, 0, 0, 0.05);
  padding: 0 16px;
}

.tab-item {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  font-size: 14px;
  color: #999;
  transition: color 0.3s;
}

.tab-item.active {
  color: #007aff;
}

.page-container {
  flex: 1;
  overflow-y: auto;
  background-color: #f5f5f5;
}
</style>
