<script setup>
import { ref } from "vue";
import ModelMyComponent from "./ModelMyComponent.vue";

const myText = ref("");
</script>

<template>
  <h3>v-model:title.capitalize</h3>
  This input capitalizes everything you enter:
  <ModelMyComponent v-model:title.capitalize="myText" />
</template>