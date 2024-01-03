<template>
  <h3>Transition 组件</h3>
  <button @click="show = !show">Toggle</button>
  <Transition>
    <p v-if="show">hello</p>
  </Transition>
</template>

<script setup>
import { ref } from "vue";
const show = ref(true);
</script>

<style>
/**
 * .v-enter-active 和 .v-leave-active 选择器
 * 这两个选择器定义了过渡效果应用于哪个元素
 * { transition: opacity 0.5s ease; }
 * 这个属性定义了过渡效果的类型、持续时间和缓动函数
 * 过渡效果是 opacity 的变化
 * 0.5s 表示过渡效果的持续时间是0.5秒
 * ease 表示缓动函数是缓入缓出的

/**
 * .v-enter-from 和 .v-leave-to 选择器
 * 这两个选择器定义了过渡效果的起始状态和结束状态
 * { opacity: 0; }
 * 这个属性定义了元素的透明度的起始值和结束值
 * 在过渡效果开始和结束时，元素的透明度将从 0 变化到 0
 * 即元素在开始动画和结束动画时将完全透明
 */
.v-enter-active,
.v-leave-active {
  transition: opacity 1.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>



