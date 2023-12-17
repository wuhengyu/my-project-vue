<script setup>
import { ref } from "vue";
const items = ref([{ message: "Foo" }, { message: "Bar" }]);
const items2 = ref([{ message: "Foo" }, { message: "Foo" }]);
const parentMessage = ref("Parent");
const items3 = ref([{ message: "Foo" }, { message: "Bar" }]);

const items4 = [{ message: "Foo" }, { message: "Bar" }];
items4.forEach((items, index) => {
  // 可以访问外层的 `parentMessage`
  // 而 `item` 和 `index` 只在这个作用域可用
  console.log(parentMessage, items.message, index);
});
</script>

<template>
  <h1>App8</h1>
  <h3>items 不带key</h3>
  <li v-for="item in items">
    {{ item.message }}
  </li>
  <h3>items 带key</h3>
  <!-- 为 v-for 循环中的每个项添加一个 :key 属性，以确保每个循环项都有唯一的标识符 -->
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
  <h3>items没有唯一的属性</h3>
  <!-- item2相同的话，并不会确保每个循环项都具有唯一的标识符。两个循环项具有相同的 message 值，它们的 key 值也是相同的。 -->
  <li v-for="item2 in items2" :key="item2.message">
    {{ item2.message }}
  </li>
  <!-- 没有唯一的属性可供使用，使用索引值作为 key， index 是循环的索引值 -->
  <li v-for="item2 in items2" :key="item2.index">
    {{ item2.message }}
  </li>

  <h3>items可选的第二个参数表示当前项的位置索引</h3>
  <li v-for="(item3, index) in items3">
    {{ parentMessage }} - {{ index }} - {{ item3.message }}
  </li>
</template>