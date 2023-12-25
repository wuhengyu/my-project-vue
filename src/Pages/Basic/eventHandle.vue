<script setup>
import { ref } from "vue";
const count = ref(0);

const name = ref("Vue.js");
function greet(event) {
  alert(`Hello ${name.value}!`);
  // `event` 是 DOM 原生事件
  if (event) {
    alert(event.target.tagName);
  }
}

function say(message) {
  alert(message);
}

function warn(message, event) {
  // 这里可以访问原生事件
  if (event) {
    event.preventDefault();
  }
  alert(message);
}
</script>

<template>
  <h1>App9</h1>
  <!-- 内联事件处理器 -->
  <button @click="count++">Add 1</button>
  <p>Count is: {{ count }}</p>

  <!-- 方法事件处理器 -->
  <!-- `greet` 是上面定义过的方法名 -->
  <button @click="greet">Greet</button>

  <!-- 在内联处理器中调用方法 -->
  <button @click="say('hello')">Say hello</button>
  <button @click="say('bye')">Say bye</button>

  <!-- 在内联事件处理器中访问事件参数 -->
  <!-- 使用特殊的 $event 变量 -->
  <button @click="warn('Form cannot be submitted yet.', $event)">
    Submit1
  </button>
  <!-- 使用内联箭头函数 -->
  <button @click="(event) => warn('Form cannot be submitted yet.', event)">
    Submit2
  </button>

  <!-- 事件修饰符 -->
  <!-- 单击事件将停止传递 -->
  <a @click.stop="doThis"></a>
  <!-- 提交事件将不再重新加载页面 -->
  <form @submit.prevent="onSubmit"></form>
  <!-- 修饰语可以使用链式书写 -->
  <a @click.stop.prevent="doThat"></a>
  <!-- 也可以只有修饰符 -->
  <form @submit.prevent></form>
  <!-- 仅当 event.target 是元素本身时才会触发事件处理器 -->
  <!-- 例如：事件处理器不来自子元素 -->
  <div @click.self="doThat">...</div>
  <!-- 添加事件监听器时，使用 `capture` 捕获模式 -->
  <!-- 例如：指向内部元素的事件，在被内部元素处理前，先被外部处理 -->
  <div @click.capture="doThis">...</div>
  <!-- 点击事件最多被触发一次 -->
  <a @click.once="doThis"></a>
  <!-- 滚动事件的默认行为 (scrolling) 将立即发生而非等待 `onScroll` 完成 -->
  <!-- 以防其中包含 `event.preventDefault()` -->
  <div @scroll.passive="onScroll">...</div>
</template>