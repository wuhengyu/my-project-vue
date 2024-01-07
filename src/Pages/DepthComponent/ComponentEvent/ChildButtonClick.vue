<!-- 子组件 -->  
<script setup>
// 在 Vue 3 中，defineProps 是一个编译器宏，这意味着它不需要被显式地导入
// 允许你在组件中直接使用一些特殊的函数，如 defineProps 和 defineEmits
// 编译器宏在编译时会自动处理这些函数
// import { defineEmits } from "vue";

const emit = defineEmits(["inFocus", "submit"]);

function submitButtonClick() {
  emit("submit", "1111");
}

function inFocusButtonClick() {
  emit("inFocus");
}
</script>  
  
<!-- 模板 -->  
<template>
  <button @click="submitButtonClick">点击我submit</button>
  <button @click="inFocusButtonClick">点击我inFocus</button>
</template>