<!-- 定义一个组件 -->
<template>
  <br /><br />
  <button @click="count++">You clicked me {{ count }} times.</button>
</template>

<script setup>
import { ref } from "vue";
const count = ref(0);
</script>


