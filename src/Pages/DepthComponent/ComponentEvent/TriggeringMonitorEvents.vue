<template>
  <h3>触发与监听事件</h3>
  <!-- 每次点击触发 -->
  <!-- 父组件可以通过 v-on (缩写为 @) 来监听事件 -->
  <MyComponent @some-event="callback" />
  <!-- 只触发一次 -->
  <!-- 当按钮被点击时，它会调用 $emit 方法，并将事件名称 'someEvent' 作为参数传递给它。
  这会触发父组件中的事件监听器，并执行相应的回调函数 -->
  <!-- 父组件可以通过 @some-event 来监听该事件，并在触发时执行相应的回调函数。 -->
  <MyComponent @some-event.once="callback" />
</template>

<script setup>
import MyComponent from "./MyComponent.vue";

const callback = (payload) => {
  // 在这里处理事件回调
  // console.log("触发了 some-event 事件，携带的数据为:", payload);
  alert("触发了 some-event 事件，携带的数据为:" + payload);
};
</script>