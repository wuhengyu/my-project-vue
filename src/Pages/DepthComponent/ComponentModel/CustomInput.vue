<!-- CustomInput.vue -->
<script setup>
// 定义Props属性，用于接收父组件传递的modelValue值
defineProps(["modelValue"]);

// 定义Emits方法，用于将更新modelValue的值通过$emit方法发出
defineEmits(["update:modelValue"]);
</script>

<template>
  <!-- 接收一个名为modelValue的属性从父组件传递，并将其值渲染为一个输入框 -->
  <!-- 当输入框的值发生变化时，通过$emit方法触发update:modelValue事件 -->
  <!-- 将输入框的值作为参数传递给父组件，使父组件的modelValue属性更新为新的值。 -->
  <!-- 访问事件对象（$event）的 target 属性获取到的输入框的当前值 -->
  <!-- 将获取到的值作为参数传递给 $emit 方法，用于触发名为 'update:modelValue' 的自定义事件，并将新的值传递给父组件进行处理或更新s -->
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>