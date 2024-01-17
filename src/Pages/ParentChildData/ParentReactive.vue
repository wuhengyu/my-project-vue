<template>
  <div>
    home
    <ChildReactive :arrun="arrun"></ChildReactive>
    <ChildReactive :arrun="arrun2"></ChildReactive>
    <ChildReactive :arrun="arrun3"></ChildReactive>
    <button @click="updateArrun">reactive修改 arrun</button>
    <button @click="updateArrun2">普通修改 arrun2</button>
    <button @click="updateArrun3">ref修改 arrun3</button>
  </div>
</template>
<script setup>
import ChildReactive from "./ChildReactive.vue";
import { reactive, ref } from "vue";

// 传递的数据，使用reactive会响应式更新视图
// reactive 函数将一个普通的 JavaScript 对象转换为响应式对象。这意味着当对象的属性发生变化时，Vue 会自动检测到变化并更新相关的视图。
const arrun = reactive({
  title: "张三",
  age: 18,
  sex: "男",
});

// 一个普通的 JavaScript 对象，它不是响应式的。这意味着当你修改 arrun2 对象的属性时，Vue 不会自动检测到变化并更新视图。
const arrun2 = {
  title: "张三21",
  age: 182,
  sex: "男2",
};

const arrun3 = ref({
  title: "张三21",
  age: 182,
  sex: "男2",
});

const updateArrun = () => {
  arrun.age = 200;
};

const updateArrun2 = () => {
  arrun2.age = 200;
};

const updateArrun3 = () => {
  arrun3.value.age = 200;
};
</script>


<!-- ref 和 reactive 是 Vue 3 Composition API 提供的两个函数，用于创建响应式数据。

ref:
ref 用于创建一个包装器对象（Wrapper Object），将一个普通的 JavaScript 值转换为响应式对象。
当我们使用 ref 创建的对象时，需要通过 .value 来访问和修改其内部的值。
ref 创建的对象是透明的，即在模板中使用时，不需要访问 .value，Vue 会自动解包并追踪其依赖。
适用于包装简单的基本类型（如数字、字符串等）。
reactive:
reactive 用于将一个普通的 JavaScript 对象转换为响应式对象。
当我们使用 reactive 创建的对象时，可以直接访问和修改其属性，无需额外的 .value。
reactive 创建的对象是透明的，Vue 会追踪其内部所有的属性，并在属性发生变化时更新视图。
适用于包装复杂的对象和嵌套结构。

ref 适用于简单的基本类型，需要通过 .value 来访问和修改值。
reactive 适用于普通的 JavaScript 对象和复杂的数据结构，可以直接访问和修改属性。 -->