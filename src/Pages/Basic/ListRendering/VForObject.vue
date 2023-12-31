<template>
  <h3>v-for 与对象</h3>
  <ul>
    <li v-for="value in myObject" :key="value">
      {{ value }}
    </li>
  </ul>
</template>

<script setup>
import { reactive } from "vue";
const myObject = reactive({
  title: "How to do lists in Vue",
  author: "Jane Doe",
  publishedAt: "2016-04-10",
});
</script>