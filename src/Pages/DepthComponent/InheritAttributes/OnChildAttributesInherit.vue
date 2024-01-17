<template>
  <div v-bind="attrs" @click="emitEvent">子组件内容</div>
  <div v-bind="$attrs" @click="emitEvent">子组件内容</div>
  <div>{{ name }}</div>
</template>

<script setup>
import { useAttrs, defineEmits } from "vue";

const props = defineProps({
  name: String,
  age: Number,
});
const attrs = useAttrs();
const emit = defineEmits(["myEvent"]);

const emitEvent = () => {
  console.log("Child click event");
  emit("myEvent", "Hello from child!");
};
</script>