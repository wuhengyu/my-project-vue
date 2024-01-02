<template>
  <h3>基于 CSS 的过渡效果</h3>
  <button @click="show = !show">Toggle Slide + Fade</button>
  <br /><br /><br />
  <Transition name="slide-fade">
    <p v-if="show">hello</p>
  </Transition>
</template>

<script setup>
import { ref } from "vue";
const show = ref(true);
</script>

<style>
/*
  进入和离开动画可以使用不同
  持续时间和速度曲线。
*/
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(100px);
  opacity: 0;
}
</style>