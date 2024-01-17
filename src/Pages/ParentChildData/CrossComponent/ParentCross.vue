<template>
  <h3>跨组件通信</h3>
  <div>
    <ChildCross></ChildCross>
  </div>
</template>
<script setup>
import ChildCross from "./ChildCross.vue";
import { ref, provide } from "vue";
const num = ref("父组件的数据");
// provide传递
provide("num", num);
</script>