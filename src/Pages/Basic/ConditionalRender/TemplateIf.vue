<template>
  <div v-if="ok1">
    <h1>Title1</h1>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
  </div>

  <div v-if="ok2">
    <h1>Title2</h1>
    <p>Paragraph 11</p>
    <p>Paragraph 22</p>
  </div>
</template>

<script setup>
// import { ref } from "vue";
// const ok1 = ref(true);
// 或者
const ok1 = false;
const ok2 = true;
</script>