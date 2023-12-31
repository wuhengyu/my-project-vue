<template>
  <h3>v-if</h3>
  <h1 v-if="awesome">Vue is awesome!</h1>

  <h3>v-else</h3>
  <button @click="awesome = !awesome">Toggle</button>
  <h3 v-if="awesome">Vue is awesome!</h3>
  <h3 v-else>Oh no 😢</h3>

  <h3>v-else-if</h3>
  <div v-if="type === 'A'">A</div>
  <div v-else-if="type === 'B'">B</div>
  <div v-else-if="type === 'C'">C</div>
  <div v-else>Not A/B/C</div>
</template>

<script setup>
import { ref } from "vue";
const awesome = ref(true);
</script>