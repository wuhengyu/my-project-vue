<template>
  <h3>
    <!-- ref 函数返回一个带有 value 属性的对象，通过访问 ref 对象的 value
    属性来读取或修改值。当使用 ref 创建的响应式值发生变化时，会触发响应式更新。 -->

    父组件通过对子组件绑定ref
  </h3>
  <div>
    <!-- ref是父访问子实例和数据 -->
    <!-- ref="arr" 给子组件 <ChildRef> 添加了一个引用名为 "arr" 的引用信息 -->
    <!-- 父组件就可以通过这个引用名来访问子组件实例。 -->
    <!-- ref属性是用于给DOM元素或子组件注册一个引用信息 -->

    <!-- ：是父传递数据，子通过props接收 -->
    <!-- :是动态绑定语法，表示这里的数据是动态的 -->
    <!-- :arr2实际上传递的是名为arr2的属性（prop），值来自于父组件自身的数据属性arr2，父组件将其数据对象中的arr2属性值传递给了子组件的arr2 prop -->
    <!-- : 将父组件的 arr2 数据属性的值传递给子组件的 arr2 prop -->
    <!-- 子组件就可以接收和使用父组件传递的数据 -->
    <ChildRef ref="arr" :arr2="arr2"></ChildRef>
    <button @click="add">点我ref获取</button>
  </div>
</template>
<script setup>
import ChildRef from "./ChildRef.vue";
import { ref, reactive } from "vue";
// 通过ref来获取子组件数据和方法
// ref 用于定义单个响应式值，而 reactive 则用于定义包含多个属性的响应式对象
const arr = ref(null);

// reactive 则用于定义包含多个属性的响应式对象。它接受一个普通的 JavaScript 对象，并将对象的所有属性转换为响应式属性。
// 通过访问响应式对象的属性时，会自动追踪依赖，并在属性发生变化时触发更新。与 ref 不同，不需要通过 .value 来访问属性值。
// 传递的数据
const arr2 = reactive({
  title: "张三",
  age: 18,
  sex: "男",
});
const add = () => {
  // 使用 arr.value 来获取子组件ChildRef的实例，并通过实例访问 shuzu 属性。
  alert(arr.value.shuzu);
  alert(arr.value.shuzu2);

  // 打印reactive的值
  console.log(arr2.title);
  console.log(arr2.age);
  console.log(arr2.sex);

  // 打印arr实例
  // console.log("arr", arr);

  // 已经过时，不再使用
  // console.log(this.$refs.arr);
};
</script>