<template>
  <!-- 触发与监听事件 -->
  <!-- MyComponent -->
  <br /><br />
  <!-- 每次点击触发 -->
  <button @click="$emit('someEvent')">click me</button>
  <!-- 父组件可以通过 v-on (缩写为 @) 来监听事件 -->
  <MyComponent @some-event="callback" />
  <!-- 只触发一次 -->
  <MyComponent @some-event.once="callback" />
</template>

<script setup>
import MyComponent from "./MyComponent.vue";

const callback = (payload) => {
  // 在这里处理事件回调
  console.log("触发了 some-event 事件，携带的数据为:", payload);
};
</script>