<template>
  <div>
    <input type="text" v-model="email" placeholder="Email" />
    <input type="password" v-model="password" placeholder="Password" />
    <button @click="submitForm">Submit</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

// 定义组件接收的props
const props = defineProps({
  email: String,
  password: String,
});

// 定义组件发出的emit
const emit = defineEmits({
  // 没有校验的click事件
  click: null,

  // submit 事件定义了一个校验函数，该函数接收一个包含 email 和 password 属性的对象参数。
  // 如果 email 和 password 都存在，将弹出一个成功的提示框并返回 true，否则将打印一个警告信息并返回 false。
  // 有校验的submit事件
  submit: ({ email, password }) => {
    if (email && password) {
      alert("Success");
      return true;
    } else {
      console.warn("Invalid submit event payload!");
      return false;
    }
  },
});

// 提交表单的函数
function submitForm() {
  // 用 emit 方法触发 submit 事件，并传递一个包含 email 和 password 属性的对象作为参数
  emit("submit", { email, password });
}

// 初始化email和password
// 如果这些 prop 未被传递，则它们的值为空字符串
let email = props.email || "";
let password = props.password || "";
</script>