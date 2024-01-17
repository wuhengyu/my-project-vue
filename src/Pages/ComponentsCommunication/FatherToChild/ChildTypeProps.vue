<script setup>
// defineProps用于声明组件接收的props（属性），而defineComponent用于创建一个组件
import { defineProps, defineComponent } from "vue";

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
        console.warn("用户名校验失败");
        return false;
      }
    },
  },
  uid: [Number, String],
});

// defineComponent 函数用于创建组件，并且在组件配置对象中声明的属性会自动成为组件的实例属性。这意味着在组件内部，可以直接通过属性名（如 title、index、userName 和 uid）来访问这些属性
defineComponent({
  // 组件的 props
  props: {
    // 可选，并提供默认值
    title: {
      type: String,
      required: false,
      default: "默认标题",
    },

    // 默认可选，单类型
    index: Number,

    // 添加一些自定义校验
    userName: {
      type: String,

      // 在这里校验用户名必须至少 3 个字
      // validator: (v) =>
      //   v.length >= 3
      //     ? console.log("用户名校验通过")
      //     : console.log("用户名校验失败"),
      validator: (value) => {
        if (value.length >= 3) {
          return true; // 校验通过
        } else {
          console.warn("用户名校验失败"); // 控制台显示警告信息
          return false; // 校验不通过
        }
      },
    },

    // 默认可选，但允许多种类型
    uid: [Number, String],
  },
});
</script>

<!-- 为了区分组件的属性和普通的数据变量，需要使用 props 对象来访问组件的 props 属性 -->
<template>
  <div>
    <p>{{ props.title }}</p>
    <p>Welcome, {{ props.userName }}!</p>
    <p>Index: {{ props.index }}</p>
    <p>UID: {{ props.uid }}</p>
  </div>
  <div>
    <p>标题：{{ title }}</p>
    <p>索引：{{ index }}</p>
    <p>用户id：{{ uid }}</p>
    <p>用户名：{{ userName }}</p>
  </div>
</template>