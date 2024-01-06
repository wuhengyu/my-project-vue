<template>
  <h3>事件参数</h3>
  <EventButton @increase-by="(n) => (count += n)" />
  <!-- 自定义回调函数increaseCount处理事件的 payload（数据） -->
  <EventButton @increase-by="increaseCount" />
  <p>Count: {{ count }}</p>
</template>

<script setup>
import EventButton from "./EventButton.vue";
import { ref } from "vue";
const count = ref(0);
function increaseCount(n) {
  count.value += n;
  console.log(count.value);
  alert("触发了 increaseBy 事件，携带的数据为:" + n);
}
</script>