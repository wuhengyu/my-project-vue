<!--
可定制插槽和 CSS 过渡效果的模态框组件。
-->

<script setup>
import Modal from "./Modal.vue";
import { ref } from "vue";

const showModal = ref(false);
</script>

<template>
  <h3>将 Teleport 和 Transition 结合使用来创建一个带动画的模态框</h3>
  <button id="show-modal" @click="showModal = true">Show Modal</button>

  <Teleport to="body">
    <!-- 使用这个 modal 组件，传入 prop -->
    <modal :show="showModal" @close="showModal = false">
      <template #header>
        <h3>custom header</h3>
      </template>
    </modal>
  </Teleport>
</template>