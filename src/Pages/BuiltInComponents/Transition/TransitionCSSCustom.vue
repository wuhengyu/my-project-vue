<script setup>
import { ref } from "vue";

const show = ref(true);
</script>

<template>
  <h3>自定义过渡 class</h3>
  <button @click="show = !show">Toggle</button>
  <Transition
    name="custom-classes"
    enter-active-class="animate__animated animate__tada"
    leave-active-class="animate__animated animate__bounceOutRight"
  >
    <p v-if="show">hello</p>
  </Transition>
</template>

<!-- 这段代码是一个 Vue 组件，展示了一个简单的过渡效果。组件的模板部分包含了一个标题、一个按钮和一个过渡组件。
当按钮被点击时，show 变量的值会被取反，从而控制过渡的开启和关闭。
过渡组件包裹了一个条件渲染的段落元素，当 show 变量为 true 时，该段落元素会被显示出来。
过渡组件设置了两个 active class，即进入过渡时和离开过渡时要应用的动画 class。
在这个例子中，进入过渡时应用的动画是 "animate__animated animate__tada"，离开过渡时应用的动画是 "animate__animated animate__bounceOutRight"。
这些动画 class 是从 animate.css 框架中导入的。
在样式部分，使用了 @import 规则导入了 animate.css 框架的 minified 文件，以使用其中的动画效果。 -->

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";
</style>
