<script setup>
// defineProps用于声明组件接收的props（属性），而defineComponent用于创建一个组件
import { defineProps } from "vue";

// 为了访问组件的 props 属性，需要使用 props 对象来访问它们
// defineProps 用于声明组件接收的 props
// const props = defineProps({
//   title: String,
//   index: Number,
//   userName: String,
//   uid: Number,
// });

// 或者使用对象语法声明 props
// 自定义验证函数会在这里被触发，并且警告信息会在控制台中显示
const props = defineProps({
  title: {
    type: String,
    default: "默认标题",
  },
  index: Number,
  userName: {
    type: String,
    validator: (value) => {
      if (value.length >= 3) {
        return true;
      } else {
        console.warn("defineProps, 我的用户名校验失败");
        return false;
      }
    },
  },
  uid: [Number, String],
});
</script>

<!-- 为了区分组件的属性和普通的数据变量，需要使用 props 对象来访问组件的 props 属性 -->
<template>
  <div>
    <!-- 使用 props 对象可以更清晰地表达该值是来自组件的属性 -->
    <p>{{ props.title }}</p>
    <p>Welcome, {{ props.userName }}!</p>
    <p>Index: {{ props.index }}</p>
    <p>UID: {{ props.uid }}</p>
  </div>
  <div>
    <!-- 直接访问属性时，属性名可以直接使用，不需要通过 props 对象来访问 -->
    <!-- 使用 defineProps 声明属性时，会将这些属性自动添加到组件的实例属性中，所以可以直接通过属性名访问。 -->
    <p>标题：{{ title }}</p>
    <p>索引：{{ index }}</p>
    <p>用户id：{{ uid }}</p>
    <p>用户名：{{ userName }}</p>
  </div>
</template>