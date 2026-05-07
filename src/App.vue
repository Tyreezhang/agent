<template>
  <!-- 纯原生 SDK 容器，全屏显示 -->
  <div id="ai-chat" class="sdk-container"></div>
</template>

<script setup>
import { onMounted } from 'vue'

// 你的智能体 ID
const projectId = '7636980458764615707'

onMounted(() => {
  // 加载 SDK
  const script = document.createElement('script')
  script.src = 'https://lf-cdn.coze.cn/obj/unpkg/latest/coze/web-sdk/dist/js-umd/index.min.js'
  script.onload = initSDK
  document.body.appendChild(script)
})

// 初始化 SDK（纯原生、无自定义样式冲突）
function initSDK() {
  window.cozeWebSDK.init({
    projectId: projectId,
    refreshToken: () => Promise.resolve(import.meta.env.VITE_COZE_TOKEN),
    // 原生主题：dark 深色 / light 浅色
    config: {
      theme: 'dark'
    }
  })
}
</script>

<style scoped>
/* 仅设置全屏，不干扰 SDK 样式 */
.sdk-container {
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
