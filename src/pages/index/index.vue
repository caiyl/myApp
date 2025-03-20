<template>
  <div class="container">
    <!-- 主要内容区域 -->
    <div class="content">
      <div v-if="activeTab === 0">
        <h1>首页内容</h1>
      </div>
      <div v-else-if="activeTab === 1">
        <h1>发现页内容</h1>
      </div>
      <div v-else-if="activeTab === 2">
        <h1>我的页面内容</h1>
      </div>
    </div>

    <!-- 底部导航栏 -->
    <div class="tab-bar">
      <div class="tab-container">
        <button
          v-for="tab in tabs"
          :key="tab.id"
          @click="activeTab = tab.id"
          class="tab-item"
          :class="{ 'active': activeTab === tab.id }"
        >
          {{ tab.title }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HomeView from '../../views/HomeView.vue'
import DiscoverView from '../../views/DiscoverView.vue'
import ProfileView from '../../views/ProfileView.vue'

const activeTab = ref(0)

const tabs = [
  { id: 0, title: '首页', component: HomeView },
  { id: 1, title: '发现', component: DiscoverView },
  { id: 2, title: '我的', component: ProfileView }
]
</script>

<style scoped>
.container {
  min-height: 100vh;
  position: relative;
  padding-bottom: 50px; /* 为底部导航栏留出空间 */
}

.content {
  padding: 16px;
}

.tab-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 50px;
  background-color: rgb(255, 255, 255);
  border-top: 1px solid #eee;
  z-index: 1000;
}

.tab-container {
  display: flex;
  flex-direction: row;
  height: 100%;
}

.tab-item {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #666;
  font-size: 10px;
  text-align: center;
  margin-top: 1px; 
}

.tab-item.active {
  color: #3498db; /* 激活状态的颜色 */
}
</style>
