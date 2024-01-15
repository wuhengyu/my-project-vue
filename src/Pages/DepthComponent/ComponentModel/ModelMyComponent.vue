<script setup>
const props = defineProps(["title", "titleModifiers"]);
defineEmits(["update:title"]);

// console.log(props.titleModifiers); // { capitalize: true }
</script>

<template>
  <input
    type="text"
    :value="title"
    @input="$emit('update:title', $event.target.value)"
  />
</template>