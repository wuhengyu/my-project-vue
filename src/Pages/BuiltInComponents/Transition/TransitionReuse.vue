<script setup>
import { ref } from "vue";

const docState = ref("saved");
</script>

<!-- 这段代码是一个Vue模板，包含了一个可复用的过渡效果。整个模板展示了一个标题和一组按钮，用户可以通过点击按钮在不同的状态之间切换。
  过渡效果使用了名为"slide-up"的动画，使得元素在切换状态时以滑动的方式进行过渡。
模板中使用了<Transition>指令来包裹包含过渡效果的元素。通过设置name属性，指定了使用的过渡效果的名称为"slide-up"。
  在过渡效果范围内，根据docState的值显示不同的按钮，并且设置了按钮的点击事件，当按钮被点击时，通过@click事件更新docState的值，从而改变状态。
整个模板使用了Vue的指令和属性来实现可复用的过渡效果，使得状态切换更加平滑和吸引人。 -->

<template>
  <h3>可复用过渡效果</h3>
  <span style="margin-right: 20px">Click to cycle through states:</span>
  <div class="btn-container">
    <Transition name="slide-up">
      <button v-if="docState === 'saved'" @click="docState = 'edited'">
        Edit
      </button>
      <button v-else-if="docState === 'edited'" @click="docState = 'editing'">
        Save
      </button>
      <button v-else-if="docState === 'editing'" @click="docState = 'saved'">
        Cancel
      </button>
    </Transition>
  </div>
</template>

<style>
.btn-container {
  display: inline-block;
  position: relative;
  height: 1em;
}

/* button {
  position: absolute;
}

.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.25s ease-out;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateY(30px);
}

.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
} */
</style>