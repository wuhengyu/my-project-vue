<template>
  <h1 v-show="ok1">Hello!</h1>
  <h1 v-show="ok2">World!</h1>
</template>

<script setup>
const ok1 = true;
const ok2 = false;
</script>