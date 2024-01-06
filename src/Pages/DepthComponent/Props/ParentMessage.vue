<template>
  <h3>父组件传递数据给子组件</h3>
  <div>
    <props-child-component :message="parentMessage" />
  </div>
</template>

<!-- <script>
import PropsChildComponent from "./PropsChildComponent.vue";

export default {
  components: {
    PropsChildComponent,
  },
  data() {
    return {
      parentMessage: "Hello from parent component",
    };
  },
};
</script> -->

<script setup>
import PropsChildComponent from "./PropsChildComponent.vue";
const parentMessage = "Hello from parent component";
</script>