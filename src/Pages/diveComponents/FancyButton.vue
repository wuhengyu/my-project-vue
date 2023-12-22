<template>
  <button class="fancy-btn">
    <!-- 通过使用插槽，<FancyButton> 仅负责渲染外层的 <button> (以及相应的样式)，而其内部的内容由父组件提供。 -->
    <slot />
  </button>
</template>
<style>
.fancy-btn {
  color: #fff;
  background: linear-gradient(315deg, #42d392 25%, #647eff);
  border: none;
  padding: 5px 10px;
  margin: 5px;
  border-radius: 8px;
  cursor: pointer;
}
</style>