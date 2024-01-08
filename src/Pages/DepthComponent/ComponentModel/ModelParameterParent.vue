<template>
  <div>
    <!-- v-model 的参数 -->
    <h3>{{ title }}</h3>
    <ModelParameterChild v-model:title="title" />
  </div>
</template>

<script setup>
import ModelParameterChild from "./ModelParameterChild.vue";
const title = ref("v-model 的参数");
import { ref } from "vue";
</script>