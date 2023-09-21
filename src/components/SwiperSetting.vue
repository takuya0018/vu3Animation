<template>
  <div class="setting">
    <Swiper :modules="[Autoplay]" :autoplay="{delay: 1500,  disableOnInteraction: false,}" :speed="1000" :loop="true">
      <SwiperSlide v-for="(item, index) in slideItems" :key="index">
        <img :src="require(`../assets/${item}`)" alt="">
      </SwiperSlide>
    </Swiper>
  </div>
</template>

<script lang="ts" setup>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination, Navigation } from 'swiper/modules';

// Import Swiper styles
import 'swiper/css';
import 'swiper/scss/pagination';
import 'swiper/scss/navigation';

const slideItems:string[] = [
  'bg-01.jpg',
  'bg-02.jpg',
  'bg-03.jpg',
]
</script>

<style lang="scss">
.swiper{
  width: 100%;
  height: auto;
  overflow: hidden;
  .swiper-slide{
    img {
      width: 100%;
      height: 100%;
    }
  }
}
</style>