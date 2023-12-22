<!-- MyComponent.vue -->

<template>
  <div>
    <button @click="handleClick" class="fancy-btn">点击我触发事件</button>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick() {
      // 在这里触发事件并传递数据
      this.$emit("some-event", "Hello, World!");
    },
  },
};
</script>

<style scoped>
/* 可选的样式规则 */
.fancy-btn {
  color: #fff;
  background: linear-gradient(315deg, #1135d3 25%, #ff64c4);
  border: none;
  padding: 5px 10px;
  margin: 5px;
  border-radius: 8px;
  cursor: pointer;
}
</style>