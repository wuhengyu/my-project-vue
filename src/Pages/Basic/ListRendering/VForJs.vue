<template>
  <h3>v-for</h3>
  <button @click="addItem1">button1</button>
  <button @click="addItem2">button2</button>
</template>

<script setup>
import { ref } from "vue";
const parentMessage = "Parent";
const items = ref([{ message: "Foo" }, { message: "Bar" }]);
const items2 = ["Foo", "Bar"];

function addItem1() {
  // 循环打印数组中的每个元素
  for (let i = 0; i < items.value.length; i++) {
    console.log(items.value[i].message);
    console.log("1----------------");
  }
  // 循环打印数组中的每个元素
  for (let i = 0; i < items2.length; i++) {
    console.log(items2[i]);
    console.log("2----------------");
  }
}

function addItem2() {
  // 打印ref引用数组中的每个元素
  items.value.forEach((item, index) => {
    // 可以访问外层的 `parentMessage`
    // 而 `item` 和 `index` 只在这个作用域可用
    console.log(parentMessage, item.message, index);
  });

  console.log("3----------------");

  // 打印普通数组中的每个元素
  if (Array.isArray(items)) {
    items.forEach((item, index) => {
      console.log(parentMessage, item.message, index);
    });
  } else {
    console.log("items is not an array.");
  }
  console.log("4----------------");

  // 打印普通数组中的每个元素
  if (Array.isArray(items2)) {
    items2.forEach((item, index) => {
      console.log(parentMessage, item, index);
    });
  } else {
    console.log("items is not an array.");
  }
}
</script>