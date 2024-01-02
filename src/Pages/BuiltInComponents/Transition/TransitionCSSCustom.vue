<script setup>
import { ref } from "vue";

const show = ref(true);
</script>

<template>
  <h3>自定义过渡 class</h3>
  <button @click="show = !show">Toggle</button>
  <br /><br /><br />
  <Transition
    name="custom-classes"
    enter-active-class="animate__animated animate__tada"
    leave-active-class="animate__animated animate__bounceOutRight"
  >
    <p v-if="show">hello</p>
  </Transition>
</template>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";
</style>