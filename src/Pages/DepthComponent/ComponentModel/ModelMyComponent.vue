<script setup>
const props = defineProps(["title", "titleModifiers"]);
defineEmits(["update:title"]);

console.log(props.titleModifiers); // { capitalize: true }
</script>

<template>
  <input type="text" :value="modelValue" @input="emitValue" />
</template>