<script setup>
// 导入依赖库
import { ref } from "vue";
import gsap from "gsap";

// 创建一个响应式的变量show，并初始化为true
const show = ref(true);

// 进入动画之前的处理函数
function onBeforeEnter(el) {
  // 使用gsap库设置元素的样式
  gsap.set(el, {
    scaleX: 0.25, // 设置元素的缩放比例为0.25
    scaleY: 0.25, // 设置元素的缩放比例为0.25
    opacity: 1, // 设置元素的透明度为1
  });
}

// 进入动画的处理函数
function onEnter(el, done) {
  // 使用gsap库对元素进行动画效果
  gsap.to(el, {
    duration: 1, // 动画持续时间为1秒
    scaleX: 1, // 设置元素的缩放比例为1
    scaleY: 1, // 设置元素的缩放比例为1
    opacity: 1, // 设置元素的透明度为1
    ease: "elastic.inOut(2.5, 1)", // 设置动画的缓动函数为弹性函数，参数为2.5和1
    onComplete: done, // 动画完成之后执行done函数
  });
}

// 离开动画的处理函数
function onLeave(el, done) {
  // 使用gsap库对元素进行动画效果
  gsap.to(el, {
    duration: 1.3, // 动画持续时间为1.3秒
    scaleX: 1, // 设置元素的缩放比例为1
    scaleY: 1, // 设置元素的缩放比例为1
    x: 1000, // 设置元素的水平偏移量为1000
    ease: "elastic.inOut(2.5, 1)", // 设置动画的缓动函数为弹性函数，参数为2.5和1
  });
  // 在动画开始0.5秒后，设置元素的透明度为0.5，并在动画完成之后执行done函数
  gsap.to(el, {
    duration: 0.2, // 动画持续时间为0.2秒
    delay: 0.5, // 动画延迟0.5秒开始
    opacity: 0.5, // 设置元素的透明度为0.5
    onComplete: done, // 动画完成之后执行done函数
  });
}
</script>

<template>
  <h3>JavaScript 钩子</h3>
  <button @click="show = !show">Toggle</button>
  <Transition
    @before-enter="onBeforeEnter"
    @enter="onEnter"
    @leave="onLeave"
    :css="false"
  >
    <div class="gsap-box" v-if="show"></div>
  </Transition>
</template>

<style>
.gsap-box {
  background: #13d37c;
  margin-top: 20px;
  width: 60px;
  height: 60px;
  border-radius: 50%;
}
</style>
