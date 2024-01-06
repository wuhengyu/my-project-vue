<template>
  <div>
    {{ message }}
    <!-- 子组件中使用通过Props传递的数据 -->
  </div>
</template>

<!-- <script>
export default {
  props: ["message"], // 声明Props选项，指定子组件期望接收的属性
};
</script> -->

<script setup>
const props = defineProps(["message"]);
</script>