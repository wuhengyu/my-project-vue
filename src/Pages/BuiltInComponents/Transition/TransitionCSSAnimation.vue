<template>
  <h3>CSS 的 animation</h3>
  <button @click="show = !show">Toggle</button>
  <Transition name="bounce">
    <p v-if="show" style="text-align: center">
      Hello here is some bouncy text!
    </p>
  </Transition>
</template>

<script setup>
import { ref } from "vue";
const show = ref(true);
</script>

<style>
/**
 * 对于bounce-enter-active元素，应用动画bounce-in 0.5秒
 */
.bounce-enter-active {
  animation: bounce-in 0.5s;
}

/**
 * 对于bounce-leave-active元素，应用动画bounce-in 0.5秒，然后反向播放
 */
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}

/**
 * 定义动画bounce-in，从0%到100%
 */
/* 
当我们使用@keyframes动画时，可以使用animation属性来定义动画的名称。在这个例子中，我们定义了一个名为bounce-in的动画。

动画bounce-in有3个关键帧，分别对应动画的0%、50%和100%的位置。

在0%的关键帧中，我们使用transform: scale(0)将元素缩放为0，使其不可见。

在50%的关键帧中，我们使用transform: scale(2)将元素放大到2倍，使其在动画过程中暂时可见。

在100%的关键帧中，我们使用transform: scale(1)将元素缩放回原始大小，完成动画。

通过使用这个动画，我们可以在页面上创建一种元素从消失到出现的效果。 */
@keyframes bounce-in {
  0% {
    transform: scale(0); /* 缩放为0 */
  }
  50% {
    transform: scale(2); /* 缩放为2*/
  }
  100% {
    transform: scale(1); /* 缩放为1*/
  }
}
</style>