<script setup>
import { ref } from "vue";
import ModelMyComponentMul from "./ModelMyComponentMul.vue";
const first = ref("");
const last = ref("");
</script>

<template>
  <h3>{{ first }}-{{ last }}</h3>
  This input capitalizes everything you enter:
  <ModelMyComponentMul
    v-model:first-name.capitalize="first"
    v-model:last-name.uppercase="last"
  />
</template>