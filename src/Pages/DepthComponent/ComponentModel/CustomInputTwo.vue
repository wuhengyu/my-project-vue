<script setup>
import { computed } from "vue";

// 定义 Props，接收一个名为 modelValue 的参数
const props = defineProps(["modelValue"]);

// 定义 Emitted Channels，接收一个名为 update:modelValue 的参数
const emit = defineEmits(["update:modelValue"]);

// 定义 computed 属性 value
const value = computed({
  // getter 方法，返回 modelValue 属性的值
  get() {
    return props.modelValue;
  },
  // setter 方法，调用 update:modelValue 方法更新 modelValue 属性的值
  set(value) {
    emit("update:modelValue", value);
  },
});
</script>

<template>
  <!-- 在模板中，使用v-model指令将<input>元素与value计算属性进行绑定。 -->
  <!-- 当<input>的值改变时，会触发update:modelValue事件来更新modelValue属性的值。 -->
  <input v-model="value" />
</template>