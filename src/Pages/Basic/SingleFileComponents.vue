<!-- 单文件组件 -->
<script setup>
import { ref } from "vue";
const count = ref(0);
const rawHtml = ref("SingleFileComponents");
const dynamicId = "dynamicId";
const objectOfAttrs = {
  id: "container",
  class: "wrapper",
};
const number = 1;
const isButtonDisabled = true;
const ok = true;
const message = "wuhengyu";
const id = 1;

const items = [
  { id: 1, text: "内容1" },
  { id: 2, text: "内容2" },
  { id: 3, text: "内容3" },
];
</script>

<!-- <script>
export default {
  data() {
    return {
      id: 1,
    };
  },
};
</script> -->
<template>
  <h1>App2</h1>
  <button @click="count++">SingleFileComponents Count2 is: {{ count }}</button>
  <!-- 文本插值 -->
  <p>Using text interpolation: {{ rawHtml }}</p>
  <!-- 原始 HTML -->
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
  <!-- Attribute 绑定 -->
  <div v-bind:id="dynamicId">dynamicId2</div>
  <!-- v-bind:id简写 -->
  <div :id="dynamicId">dynamicId3</div>
  <!-- 布尔型 Attribute -->
  <!-- 禁用按钮 -->
  <button :disabled="isButtonDisabled">布尔型 Attribute Button</button>
  <!-- 动态绑定多个值 -->
  <div v-bind="objectOfAttrs">{{ objectOfAttrs.class }}</div>
  <div v-bind="objectOfAttrs">{{ objectOfAttrs.id }}</div>
  <div v-bind="objectOfAttrs">{{ objectOfAttrs }}</div>
  <!-- 使用 JavaScript 表达式 -->
  <p>number :{{ number + 1 }}</p>
  <p>{{ ok ? "YES" : "NO" }}</p>
  <!-- split("") 将字符串拆分成字符数组 -->
  <!-- reverse() 反转字符数组的顺序 -->
  <!-- join("")将字符数组重新组合成字符串 -->
  <!-- 反转的字符串 -->
  <p>{{ message.split("").reverse().join("") }}</p>
  <!-- HTML id="list-1" -->
  <div :id="`list-${id}`"></div>
  <!-- 循环输出 -->
  <div>
    <div v-for="item in items" :key="item.id" :id="`list-${item.id}`">
      {{ item.text }}
    </div>
  </div>
</template>

<!-- <style scoped>
button {
  font-weight: bold;
}
</style> -->