<!-- 父组件 -->  
<script setup>
import ChildButtonClick from "./ChildButtonClick.vue";

// 回调函数
const handleSubmit = (data) => {
  alert("子组件的 submit 事件被触发了！" + data);
};
</script>  
  
<!-- 模板 -->  
<template>
  <h3>声明触发的事件</h3>
  <ChildButtonClick @submit="handleSubmit" />
  <ChildButtonClick @inFocus="handleSubmit" />
</template>