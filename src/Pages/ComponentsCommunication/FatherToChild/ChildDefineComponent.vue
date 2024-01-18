<script>
import { defineComponent } from "vue";

// Child.vue
export default defineComponent({
  props: ["title", "index", "userName", "uid"],
  // 在这里需要添加一个入参
  setup(props) {
    // 该入参包含了当前组件定义的所有 props
    console.log(props);
  },
});
</script>

<!-- 为了区分组件的属性和普通的数据变量，需要使用 props 对象来访问组件的 props 属性 -->
<template>
  <div>
    <!-- 直接访问属性时，属性名可以直接使用，不需要通过 props 对象来访问 -->
    <!-- 使用 defineProps 声明属性时，会将这些属性自动添加到组件的实例属性中，所以可以直接通过属性名访问。 -->
    <p>标题：{{ title }}</p>
    <p>索引：{{ index }}</p>
    <p>用户id: {{ uid }}</p>
    <p>用户名: {{ userName }}</p>
  </div>
</template>