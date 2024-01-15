<template>
  <!-- <h3>class和style的合并 + v-on监听器继承</h3> -->
  <h1 class="ChildClass">class和style的合并 + v-on监听器继承</h1>
  <button @click="emitClick" v-bind="attrs">点击我</button>
</template>


<!-- Vue 3 选择了一种更加灵活的方式来处理这个问题。
现在如果你希望在子组件中接收并使用非 prop 的 attribute，那么需要在子组件中手动地用 v-bind="$attrs" 来绑定这些 attribute。
这样你就可以明确地决定非 prop 的属性应该被绑定到哪个元素上，以及它们应该如何被处理。 -->
<script setup>
import { defineEmits, useAttrs } from "vue";
// 触发名为click的事件，并且传递参数"hello world!"
const emit = defineEmits(["myclick"]);
const attrs = useAttrs();

const emitClick = () => {
  console.log("Child emitClick, hello world!");
  emit("myclick", "hello world!");
};
</script>