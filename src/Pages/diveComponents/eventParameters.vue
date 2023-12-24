<template>
  <!-- 父组件通过监听这个increaseBy事件，并将事件参数赋值给count变量，从而实现了对计数器的管理工作 -->
  <blog-post @increaseBy="handleIncreaseBy" />
  <blog-post @increase-by="(n) => (count += n)" />
  <p>Count: {{ count }}</p>
</template>

<script setup>
import { ref } from "vue";
import BlogPost from "./BlogPost.vue";

const count = ref(0);

function handleIncreaseBy(n) {
  count.value += n;
  console.log(count.value);
  alert("触发了 increaseBy 事件，携带的数据为:" + n);
}
</script>