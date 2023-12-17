<script setup>
import { ref } from "vue";
const isActive = ref(true);
const hasError = ref(true);
</script>

<template>
  <h1>App6</h1>
  <p>绑定 HTML class</p>
  <!-- <div :class="{ active: isActive }"></div> -->
  <!-- 显示class="static active text-danger" -->
  <div class="static" :class="{ active: isActive, 'text-danger': hasError }">
    这是一个示例文本
  </div>
</template>