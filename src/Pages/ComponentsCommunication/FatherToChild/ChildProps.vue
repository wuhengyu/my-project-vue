<script setup>
const props = defineProps(["title", "index", "userName", "uid"]);
</script>

<template>
  <div>
    <p>{{ props.title }}</p>
    <p>Welcome, {{ props.userName }}!</p>
    <p>Index: {{ props.index }}</p>
    <p>UID: {{ props.uid }}</p>
  </div>
</template>