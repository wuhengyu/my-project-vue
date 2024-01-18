<script setup>
import ChildTypeProps from "./ChildTypeProps.vue";
import { reactive } from "vue";
// 组合式API写法
// 定义响应式数据
const userInfo = reactive({
  id: 1,
  name: "ha",
});
</script>

<template>
  <ChildTypeProps
    title="用户信息"
    :index="1"
    :uid="userInfo.id"
    :user-name="userInfo.name"
  />
</template>