<template>
  <br /><br />
  <h3>内联事件处理器</h3>
  <button @click="count++">Add 1</button>
  <p>Count is: {{ count }}</p>
</template>

<script setup>
import { ref } from "vue";
const count = ref(0);
</script>