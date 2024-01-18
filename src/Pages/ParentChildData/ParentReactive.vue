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


<!-- 在 Vue 3 中，ref 和 reactive 是用来创建响应式数据的两个 API。它们都可以用来定义响应式数据，但是它们之间有一些关键的区别：

使用方式:
ref 用于创建一个响应式的引用对象，它可以是基本数据类型或者对象。使用 ref 时，你通常会得到一个包含单个属性 value 的对象，这个 value 属性是响应式的。
reactive 用于创建一个响应式对象。它通常用于将已有的对象转换为响应式对象。reactive 直接操作对象本身，而不是创建一个新的引用对象。

使用场景:
当你需要一个响应式的原始值（如字符串、数字、布尔值）时，应该使用 ref。
当你需要一个响应式的对象或数组时，应该使用 reactive。

模板中的使用:
在模板中，ref 的值会自动解包，所以你不需要使用 .value 来访问或修改它的值。
reactive 创建的对象在模板中不需要解包，可以直接访问其属性。

类型:
ref 可以接受任何类型的值作为其内部 value 属性的初始值。
reactive 只能接受对象或数组作为参数，并将其转换为响应式对象。

API 设计:
ref 是一个函数，它返回一个包含 value 属性的响应式引用对象。
reactive 也是一个函数，它返回一个响应式对象的代理。

响应式检测:
ref 通过对 value 属性的 getter 和 setter 进行操作来实现响应式。
reactive 使用 Vue 3 的 Proxy 特性来拦截对象的所有操作（get、set、delete、has 等），从而实现深度响应式。
在实际应用中，你可以根据需要选择使用 ref 还是 reactive。例如，对于表单输入这样的场景，通常会使用 ref 来创建响应式的输入值。而在处理复杂的状态对象时，reactive 会更加方便。 -->