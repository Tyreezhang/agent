<template>
  <div id="ai-chat"></div>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  const script = document.createElement('script')
  script.src = "https://lf-cdn.coze.cn/obj/unpkg/latest/coze/web-sdk/dist/js-umd/index.min.js"
  script.onload = () => {
    cozeWebSDK.init({
      projectId: '7636980458764615707',
      refreshToken: () => Promise.resolve(import.meta.env.VITE_COZE_TOKEN),
    })
  }
  document.body.appendChild(script)
})
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
}
</style>
