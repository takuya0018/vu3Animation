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
// classの初期設定
let blue = ref(false);

let option:{rootMargin:string} = {
  rootMargin: `0px 0px -300px 0px`
}
const options = ref(option);

// IntersectionObserver
const ISOSerber = new IntersectionObserver(function(e){
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
const hello = ref(); //1
const hi = ref();
onMounted(function() { //4
  const testDom = hello.value;  //2
  console.log(testDom);
  console.log(hi.value.innerHTML);
  
  // IntersectionObserverに要素を渡す
  ISOSerber.observe(testDom);
});
</script>

<style lang="scss" scoped>
.ani {
  margin-top: 1000px;
  margin-bottom: 500px;
}
.blue {
  animation: changeColor 5s ease-in forwards;
}
@keyframes changeColor {
  from {
    color: black;
  }
  to {
    color: blue;
  }
}
</style>