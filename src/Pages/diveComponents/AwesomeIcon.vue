<!-- using an emoji just for demo purposes -->
<template>
  ❤️
  <button type="submit" class="fancy-btn2">
    <slot>
      Submit
      <!-- 默认内容 -->
    </slot>
  </button>
</template>

<style>
.fancy-btn2 {
  color: #fff;
  background: linear-gradient(315deg, #8cd10c 25%, #1e2b6d);
  border: none;
  padding: 5px 10px;
  margin: 5px;
  border-radius: 8px;
  cursor: pointer;
}
</style>