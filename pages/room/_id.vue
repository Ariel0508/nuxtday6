<script setup>
const router = useRouter();
const route = useRoute();
</script>
<template>
    <h2>房型詳情頁面{{ route.fullPath }}</h2>
  <div>
  <button type="button" @click="router.go(-1)">
  回到上一頁
  </button>
  </div>
</template>
<style scoped></style>