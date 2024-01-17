<template>
  <div>title</div>
  <div>
    <p>Title: {{ arrun.title }}</p>
    <p>Age: {{ arrun.age }}</p>
    <p>Sex: {{ arrun.sex }}</p>
  </div>
</template>
<script setup>
// 通过props来接收
const props = defineProps({
  arrun: Object, //指定接收的数据类型
});
console.log(props.arrun);
</script>