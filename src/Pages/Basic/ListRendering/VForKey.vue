<template>
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
</template>

<script setup>
import { ref } from "vue";
const items = ref([{ message: "Foo" }, { message: "Bar" }]);
</script>