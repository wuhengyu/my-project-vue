<script setup>
const props = defineProps({
  modelValue: String,
  // 默认值是一个空对象
  modelModifiers: { default: () => ({}) },
});

console.log(props.modelModifiers);

// 用于定义组件的输出事件。这个例子中，定义了一个update:modelValue的事件
const emit = defineEmits(["update:modelValue"]);

// 自定义函数，用于处理输入框的值。它接收一个事件对象e
function emitValue(e) {
  // 从事件对象中获取输入框的值
  let value = e.target.value;
  if (props.modelModifiers.capitalize) {
    // 获取字符串 value 的第一个字符
    // 将获取到的第一个字符转换为大写
    // 使用 slice(1) 方法获取字符串 value 从索引 1 开始到末尾的子字符串
    // 使用 + 运算符将大写化后的第一个字符和剩余的子字符串拼接在一起
    value = value.charAt(0).toUpperCase() + value.slice(1);
  }
  emit("update:modelValue", value);
}
</script>

<template>
  <!-- 将输入框的 input 事件与名为 emitValue 的处理函数进行绑定。当输入框的值发生变化时，input 事件会被触发，然后执行 emitValue 函数 -->
  <!-- 每当输入框的值发生变化时，Vue 会自动调用 emitValue 函数，并将相关的事件对象作为参数传递给该函数 -->
  <!-- 将modelValue属性绑定到输入框的值上 -->
  <input type="text" :value="modelValue" @input="emitValue" />
</template>