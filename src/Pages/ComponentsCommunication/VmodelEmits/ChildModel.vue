<template>
  <div>
    <p>uid: {{ uid }}</p>
  </div>
</template>

<script>
import { defineProps } from "vue";
export default defineProps({
  props: {
    uid: Number,
    username: String,
    age: Number,
  },
  // 注意这里的 `update:` 前缀
  emits: ["update:uid", "update:username", "update:age"],
});
</script>