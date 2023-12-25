<script setup>
import { defineProps, defineEmits } from "vue";
// defineProps 是一个仅 <script setup> 中可用的编译宏命令
// defineProps 会返回一个对象，其中包含了可以传递给组件的所有 props
const props = defineProps(["title", "id"]);
console.log(props.title);
// defineEmits 仅可用于 <script setup> 之中
defineEmits(["enlarge-text"]);
// defineProps(["title"]);

// 以 props 选项的方式声明
// export default {
//   props: ['title'],
//   setup(props) {
//     console.log(props.title)
//   }
// }
</script>

<template>
  <div class="blog-post">
    <h1>{{ id }}, {{ title }}</h1>
    <button @click="$emit('enlarge-text')">Enlarge text</button>
  </div>
</template>