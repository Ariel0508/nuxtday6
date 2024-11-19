<script setup>
import { useAsyncData } from 'nuxt/app';
const router = useRouter();
const route = useRoute();
const { data: roomsList } = await useAsyncData(
  'roomsList',
  () => $fetch(`https://nuxr3.zeabur.app/api/v1/rooms`),
  {
    transform: (response) => {
      return response.result || {};
  },
    onResponseError({ response }) {
      const { message } = response._data;
      console.error('Error:', message);
      router.push('/');
    },
  }
  ) 
</script>

<template>
  <h1>房型頁面{{ route.fullPath }}</h1>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-8 col-md-6 col-lg-3" v-for="room in roomsList" :key="room._id">
        <div class="card h-100 shadow-sm" @click="router.push(`/room/${room._id}`)">
          <img :src="room.imageUrl" class="card-img-top" alt="Room Image" />
          <div class="card-body d-flex flex-column">
            <h3 class="card-title">{{ room.name }}</h3>
            <p class="card-text flex-grow-1">{{ room.description }}</p>
            <ul class="list-unstyled">
              <li><strong>面積:</strong> {{ room.areaInfo }}</li>
              <li><strong>床型:</strong> {{ room.bedInfo }}</li>
              <li><strong>最大容納人數:</strong> {{ room.maxPeople }}</li>
              <li><strong>價格:</strong> {{ room.price }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-img-top {
  object-fit: cover;
  height: 200px;
  max-width: 100%;
}
</style>