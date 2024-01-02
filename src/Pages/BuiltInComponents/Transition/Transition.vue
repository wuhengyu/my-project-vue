<template>
  <h3>Transition 组件</h3>
  <button @click="show = !show">Toggle</button>
  <br /><br /><br />
  <Transition>
    <p v-if="show">hello</p>
  </Transition>
</template>

<script setup>
import { ref } from "vue";
const show = ref(true);
</script>

<style>
/* 下面我们会解释这些 class 是做什么的 */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>