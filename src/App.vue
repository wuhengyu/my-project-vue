<template>
  <button @click="count++">Count is: {{ count }}</button>

  <p>Using text interpolation: {{ rawHtml }}</p>
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    return {
      count: ref(0),
      rawHtml: "Hello World!",
    };
  },
};
</script>

<style>
button {
  padding: 10px 20px;
  font-size: 20px;
}
</style>