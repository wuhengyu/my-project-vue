<template>
  <div>
    home
    <!-- 事件绑定 -->
    <!-- 当 ChildEmit 组件触发名为 "add" 的自定义事件时，父组件将会调用名为 "add" 的处理函数。 -->
    <ChildEmit @add="add"></ChildEmit>
  </div>
</template>
<script setup>
import ChildEmit from "./ChildEmit.vue";

const add = (v) => {
  console.log(v.title);
};
</script>
