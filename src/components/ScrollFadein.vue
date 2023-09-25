<template>
<!-- アニメーション intersectionObserver API -->
  <div>
    <p ref="hello" class="ani" :class="{blue}">アニメーション</p>
    <p ref="hi">こんばんわ</p>
  </div>
</template>

<script lang="ts" setup>
// import文
import { ref, onMounted } from "vue";
// 変数
const hello = ref(); //1
const hi = ref();

// classの初期設定
let blue = ref(false);

// intersectionObseverのオプション
let option:{rootMargin:string} = {
  rootMargin: `0px 0px -300px 0px`
}
const options = ref(option);

// IntersectionObserver
const ISOServer = new IntersectionObserver(function(e){
  e.forEach(function(endpoint){
    console.log(endpoint);//true or false
    if(endpoint.isIntersecting == false){
      console.log("見えていない");
    }else{
      console.log("見えている");
      blue.value = true;
    }
  })
},options.value
// {
//   rootMargin: `0px 0px -300px 0px`
// }
);
// IntersectionObserverで使う要素をrefで紐付け
onMounted(function() { //4
  const testDom = hello.value;  //2
  console.log(testDom);
  console.log(hi.value.innerHTML);
  
  // IntersectionObserverに要素を渡す
  ISOServer.observe(testDom);
});
</script>

<style lang="scss" scoped>
.ani {
  margin-top: 1000px;
  margin-bottom: 500px;
  text-align: center;
  font-size: 2rem;
  opacity: 0;
  transform: translateY(100px);
}
.blue {
  animation: changeColor 2s ease forwards;
}
@keyframes changeColor {
  from {
    opacity: 0;
    transform: translateY(100px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>