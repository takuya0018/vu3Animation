<template>
  <main class="container">
    <h2>オートプレイ無限ループ</h2>
    <!-- ページネーション無し無限ループ -->
    <SwiperSetting />
    <h2>ページネーション</h2>
    <!-- ページネーション無し無限ループ -->
    <div class="item02">
      <Swiper :modules="[Pagination]" :pagination="{ clickable: false, }" :loop="true">
        <SwiperSlide v-for="(item, index) in slideItems" :key="index">
          <img :src="require(`../assets/${item}`)" alt="">
        </SwiperSlide>
      </Swiper>
    </div>
    <h2>ナビゲーション</h2>
    <!-- ナビゲーション -->
    <div class="item03">
      <Swiper :modules="[Navigation]" navigation :loop="true">
        <SwiperSlide v-for="(item, index) in slideItems" :key="index">
          <img :src="require(`../assets/${item}`)" alt="">
        </SwiperSlide>
      </Swiper>
    </div>
    <!-- アニメーション intersectionObserver API -->
    <ScrollFadein />
    <TestList />
  </main>
</template>

<script setup lang="ts">
import SwiperSetting from '@/components/SwiperSetting.vue';
import TestList from "@/components/TestList.vue";
import ScrollFadein from "@/components/ScrollFadein.vue";
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination, Navigation } from 'swiper/modules'

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

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Rubik&display=swap");


body {
  background-color: #2e4053;
  color: #fff;
  img {
    width: 100%;
    vertical-align: bottom;
  }
  h2 {
    text-align: center;
  }
  .swiper{
    width: 400px;
    height: 400px;
    overflow: hidden;
    .swiper-slide{
      img {
        width: 100%;
        height: 100%;
      }
    }
  }
  .item02 {
    .swiper{
      width: 500px;
      height: 500px;
      overflow: hidden;
      .swiper-wrapper{
        .swiper-slide{
          img {
            width: 100%;
            height: 100%;
          }
        }
      }
    }
  }
}
</style>
<style lang="scss">
.item02 {
  .swiper-pagination-bullet-active{
    background-color: #00f5e8;
  }
}
.item03{
  .swiper-button-prev {
    color: red;
  }
}
</style>