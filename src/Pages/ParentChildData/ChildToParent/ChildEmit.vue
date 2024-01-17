<template>
  <div>
    title
    <button @click="ONtil">点我传递数据给父组件</button>
  </div>
</template>
<script setup>
import { reactive } from "vue";

// 声明了本组件可以触发的自定义事件，这里声明了一个名为"add"的事件。
const emit = defineEmits(["add"]);
// 创建响应式对象
const shuzu = reactive({ title: "123" });

// 定义了一个名为ONtil的函数，当该函数被调用时（即按钮被点击时），它会触发声明过的"add"事件，并将当前的shuzu对象作为参数传递给父组件。
const ONtil = () => {
  emit("add", shuzu);
};
</script>