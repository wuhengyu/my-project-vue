<script setup>
defineProps(["title"]);
defineEmits(["update:title"]);
</script>

<template>
  <!-- $event.target.value将获取到的值作为参数传递给 $emit 方法，用于触发名为 'update:title' 的自定义事件，并将新的值传递给父组件进行处理或更新 -->
  <input
    type="text"
    :value="title"
    @input="$emit('update:title', $event.target.value)"
    class="model_input"
  />
</template>
<style>
.model_input {
  border: 1px solid #8dacf0;
  padding: 10px;
  margin: 10px;
  width: 300px;
  border-radius: 10px;
  background-color: #c8ec85;
}
</style>