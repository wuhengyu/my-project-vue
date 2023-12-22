<script setup>
import FancyButton from "./FancyButton.vue";
import AwesomeIcon from "./AwesomeIcon.vue";
</script>

<template>
  <h3>插槽内容与出口</h3>
  <br />
  <FancyButton> Click me </FancyButton>
  <FancyButton>
    <!-- 自定义内容样式 -->
    <span style="color: rgb(219, 50, 20); font-size: 30px">Click me + CSS</span>
    <!-- 还可以插入组件 -->
    <AwesomeIcon />
  </FancyButton>

  <AwesomeIcon>自定义内容</AwesomeIcon>
  <!-- 默认内容 -->
  <AwesomeIcon />
</template>

