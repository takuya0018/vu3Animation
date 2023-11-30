<template>
  <main class="container">
    <h2>オートプレイ無限ループ</h2>
    <!-- ページネーション無し無限ループ -->
      <SwiperSetting />
    <!-- アニメーション intersectionObserver API -->
    <ScrollFadein />
  </main>
</template>

<script setup lang="ts">
import SwiperSetting from '@/components/SwiperSetting.vue';
import ScrollFadein from "@/components/ScrollFadein.vue";

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
  .setting{
    width: 100%;
    height: 100vh;
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