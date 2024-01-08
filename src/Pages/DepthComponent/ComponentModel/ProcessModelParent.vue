<script setup>
import { ref } from "vue";
import ProcessModelChild from "./ProcessModelChild.vue";

const myText = ref("");
</script>

<template>
  <h3>处理 v-model 修饰符, 输入的字符串值第一个字母转为大写</h3>
  <ProcessModelChild v-model.capitalize="myText" />
</template>