<template>
  <h3>子组件向父组件提供数据shuzu和shuzu2</h3>
  <div>
    <p>Title: {{ arr2.title }}</p>
    <p>Age: {{ arr2.age }}</p>
    <p>Sex: {{ arr2.sex }}</p>
  </div>
</template>
<script setup>
import { ref } from "vue";
const shuzu = ref([1, 2, 3, 4, 5, 6, "abc"]);
const shuzu2 = ref("这是数组2");

// 通过defineExpose将数据指定抛出 父组件才可以获取需要的数据
// 通过绑定ref给子组件，父就可以访问子实例和数据
defineExpose({
  shuzu,
  shuzu2,
});

// 值来自于父组件自身的数据属性arr2，父组件将其数据对象中的arr2属性值传递给了子组件的arr2 prop
// 通过props来接收
const props = defineProps({
  arr2: Object, //指定接收的数据类型
});
console.log(props.arr2);
</script>