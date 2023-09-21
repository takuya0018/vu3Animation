<template>
  <p v-bind:class="{red}">表示</p>
</template>

<script lang="ts" setup>
import { ref } from "vue";

let red = ref(true);
</script>

<style lang="scss" scoped>
.red {
  color: red;
}
</style>