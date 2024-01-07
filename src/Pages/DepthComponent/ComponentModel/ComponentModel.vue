<template>
  <div>
    <h3>v-model 可以在组件上使用以实现双向绑定</h3>
    <p>You've searched for: {{ searchText }}</p>
    <input v-model="searchText" />
    <!-- 模板编译器会对 v-model 进行更冗长的等价展开。因此上面的代码其实等价于下面这段 -->
    <input :value="searchText" @input="searchText = $event.target.value" />
    <!-- 使用自定义组件： -->
    <CustomInput v-model="message" />{{ message }}
    <CustomInputTwo v-model="message" />{{ message }}
  </div>

  <div>
    <!-- v-model 的参数 -->
    <h1>{{ title }}</h1>
    <ModelMyComponent v-model:title="title" />
  </div>
</template>

<script setup>
import CustomInput from "./CustomInput.vue";
import CustomInputTwo from "./CustomInputTwo.vue";
import ModelMyComponent from "./ModelMyComponent.vue";
import { ref } from "vue";
const message = ref("hello");
const searchText = ref("world");
const title = ref("v-model argument example");
</script>
