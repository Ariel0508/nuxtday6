<script setup>
const route = useRoute();
// 獲取當前請求的事件
const page = ref(route.fullPath)
</script>
<template>
  <h1>404 Not Found</h1>
  <p>您尋找的 {{ page }} 頁面不存在</p>
  <NuxtLink to="/">返回首頁</NuxtLink>
</template>
<style scoped>
.not-found {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.not-found h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.not-found p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
}
</style>
