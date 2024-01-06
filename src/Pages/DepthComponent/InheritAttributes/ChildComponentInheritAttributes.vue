<!-- 子组件：MyChildComponent.vue -->
<script setup>
import { defineProps, useAttrs } from "vue";

// 定义子组件所需的props
const props = defineProps({
  importantProp: String, // 类型为字符串的prop
});

// 获取并处理所有未绑定到props的attribute
const attrs = useAttrs();
</script>

<template>
  <!-- 将所有未处理的attributes绑定到子组件的根元素上 -->
  <div v-bind="attrs">
    <!-- <div v-bind="$attrs"> -->
    <!-- 使用props -->
    <p>这是从父组件接收的重要Prop值：{{ importantProp }}</p>

    <!-- 这里的div将继承父组件传递的所有属性 -->
    <p>此div继承了父组件传递的id、class等属性。</p>
  </div>
  <div>
    <p>此div没有继承了父组件传递的id、class等属性。</p>
  </div>
</template>

<!-- 子组件中使用const attrs = useAttrs();<div v-bind="attrs">和<div v-bind="$attrs">有啥区别 
在子组件中使用 const attrs = useAttrs(); <div v-bind="attrs"> 和 <div v-bind="$attrs"> 之间有一些区别。
const attrs = useAttrs(); <div v-bind="attrs">：这种写法将通过 useAttrs() 函数获取到的父组件传递的非props属性赋值给 attrs 变量。
  然后，通过 v-bind="attrs" 将这些属性绑定到 <div> 元素上。
这意味着 <div> 元素将继承这些属性，包括父组件中的自定义属性和 Vue.js 指令。
<div v-bind="$attrs">：这种写法直接将父组件传递给子组件的非props属性（通过 $attrs）绑定到当前子组件的 <div> 元素上。
这意味着 <div> 元素将继承这些属性，包括父组件中的自定义属性和 Vue.js 指令。
这种写法不需要显式定义 const attrs = useAttrs();，而是直接使用 $attrs。
需要注意的是，$attrs 属性包含了父组件传递给子组件的所有非props属性。
而在第一种写法中，属性首先被赋值给 attrs 变量，然后再通过 v-bind="attrs" 进行绑定。
而第二种写法直接使用 $attrs 进行绑定，省略了 attrs 变量的中间步骤。
总结起来，const attrs = useAttrs(); <div v-bind="attrs"> 是先将父组件传递的非props属性赋值给 attrs 变量，再将 attrs 变量绑定到子组件的 <div> 元素上。
而 <div v-bind="$attrs"> 直接将父组件传递的非props属性绑定到子组件的 <div> 元素上，省略了中间的变量赋值步骤。  
-->