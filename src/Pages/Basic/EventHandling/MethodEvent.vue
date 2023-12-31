<template>
  <h3>方法事件处理器</h3>
  <!-- `greet` 是上面定义过的方法名 -->
  <button @click="greet">Greet</button>

  <h3>在内联处理器中调用方法</h3>
  <button @click="say('hello')">Say hello</button>
  <button @click="say('bye')">Say bye</button>

  <h3>在内联事件处理器中访问事件参数</h3>
  <!-- 使用特殊的 $event 变量 -->
  <button @click="warn('Form cannot be submitted yet.', $event)">Submit</button>
  <!-- 使用内联箭头函数 -->
  <button @click="(event) => warn('Form cannot be submitted yet.', event)">
    Submit
  </button>

  <h3>事件修饰符</h3>
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

  <h3>按键修饰符</h3>
  <!-- 仅在 `key` 为 `Enter` 时调用 `submit` -->
  <input @keyup.enter="submit" />
  <input @keyup.page-down="onPageDown" />
  <!-- 系统按键修饰符 -->
  <!-- Alt + Enter -->
  <input @keyup.alt.enter="clear" />
  <!-- Ctrl + 点击 -->
  <div @click.ctrl="doSomething">Do something</div>
  <!-- .exact 修饰符 -->
  <!-- 当按下 Ctrl 时，即使同时按下 Alt 或 Shift 也会触发 -->
  <button @click.ctrl="onClick">A</button>
  <!-- 仅当按下 Ctrl 且未按任何其他键时才会触发 -->
  <button @click.ctrl.exact="onCtrlClick">A</button>
  <!-- 仅当没有按下任何系统按键时触发 -->
  <button @click.exact="onClick">A</button>
</template>

<script setup>
import { ref } from "vue";
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
    // 阻止表单的提交，默认行为被取消
    event.preventDefault();
  }
  alert(message);
}
</script>