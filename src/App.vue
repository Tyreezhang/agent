<template>
  <div class="chat-wrap">
    <div class="chat-header">
      <span class="title">智能助手</span>
    </div>
    <div class="chat-container" id="ai-chat"></div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
const projectId = '7636980458764615707'

onMounted(() => {
  const script = document.createElement('script')
  script.src = 'https://lf-cdn.coze.cn/obj/unpkg/latest/coze/web-sdk/dist/js-umd/index.min.js'
  script.onload = initCozeSDK
  document.body.appendChild(script)
})

function initCozeSDK() {
  window.cozeWebSDK.init({
    projectId: projectId,
    refreshToken: () => Promise.resolve(import.meta.env.VITE_COZE_TOKEN)
  })
}
</script>

<style scoped>
.chat-wrap {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  background-color: #0f1419;
  overflow: hidden;
}
.chat-header {
  height: 60px;
  line-height: 60px;
  text-align: center;
  background-color: #1a232e;
  border-bottom: 1px solid #273340;
}
.title {
  font-size: 18px;
  color: #fff;
  font-weight: 500;
}
.chat-container {
  flex: 1;
  width: 100%;
  overflow: hidden;
}
</style>
