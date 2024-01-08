<template>
  <div>
    <h3>v-model 可以在组件上使用以实现双向绑定</h3>
    <h5>实现父组件与子组件的双向绑定: {{ searchText }}</h5>
    <!-- 无论选择哪种写法，确保父组件中的属性名与子组件中的 prop 名称保持一致，以确保正确的双向绑定。
    model-value 是子组件的 prop 名称，而 searchText 是父组件中的属性名 -->
    <h5>方法1：</h5>
    <input v-model="searchText" />
    <!-- 模板编译器会对 v-model 进行更冗长的等价展开。因此上面的代码其实等价于下面这段 -->
    <h5>方法2：</h5>
    <input :value="searchText" @input="searchText = $event.target.value" />
    <h5>方法3：</h5>
    <!-- 子组件传递的新值赋给父组件中的属性 -->
    <!-- 箭头函数 (newValue) => (searchText = newValue) 可以提供更多的灵活性 -->
    <CustomInput
      :model-value="searchText"
      @update:model-value="(newValue) => (searchText = newValue)"
    />
    <h5>方法4：</h5>
    <!-- 子组件传递的新值赋给父组件中的属性 -->
    <!-- $event 则是一个简洁的写法，直接将传递的新值赋给属性 -->
    <CustomInput
      :model-value="searchText"
      @update:modelValue="searchText = $event"
    />
    <h4>实现了输入框的双向绑定</h4>
    <!-- 自动监听 'update:modelValue' 事件 -->
    <!-- 新值 $event 赋给 inputValue 属性 -->
    <!-- 在输入框的值发生变化时触发'update:modelValue' 事件，同时将新的值传递给父组件 -->
    <h5>方法1：</h5>
    <CustomInput v-model="message" />{{ message }}
    <h5>方法2：</h5>
    <!-- v-model="message"相当于@update:modelValue="message = $event" -->
    <CustomInput @update:modelValue="message = $event" />{{ message }}
    <h5>方法3：</h5>
    <CustomInputTwo v-model="message" />{{ message }}
    <h5>方法4：</h5>
    <CustomInput
      :model-value="message"
      @update:model-value="(newValue) => (message = newValue)"
    />{{ message }}
  </div>
</template>

<script setup>
import CustomInput from "./CustomInput.vue";
import CustomInputTwo from "./CustomInputTwo.vue";
import { ref } from "vue";
const message = ref("hello");
const searchText = ref("world");
</script>
