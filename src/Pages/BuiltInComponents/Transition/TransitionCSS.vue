<template>
  <h3>基于 CSS 的过渡效果</h3>
  <button @click="show = !show">Toggle Slide + Fade</button>
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
/* 进入动画样式 */
.slide-fade-enter-active {
  /* 添加0.3秒的过渡效果，缓出样式 */
  transition: all 0.3s ease-out;
}
/* 离开动画样式 */
.slide-fade-leave-active {
  /* 添加0.8秒的过渡效果，自定义缓动函数 */
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

/* 进入动画初始状态 */
.slide-fade-enter-from,  
/* 离开动画结束状态  */
.slide-fade-leave-to {
  /* 平移100px */
  transform: translateX(500px);
  /* 不透明度为0 */
  opacity: 0;
}
</style>