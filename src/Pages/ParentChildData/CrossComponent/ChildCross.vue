<template>
  <div>
    子组件
    <br />
    {{ num }}
  </div>
</template>
<script setup>
import { inject } from "vue";
// inject接收
const num = inject("num");
console.log(num);
</script>