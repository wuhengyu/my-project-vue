<script setup>
defineProps({
  firstName: String,
  lastName: String,
});

defineEmits(["update:firstName", "update:lastName"]);
</script>

<template>
  <h3>多个 v-model 绑定</h3>
  <input
    type="text"
    :value="firstName"
    @input="$emit('update:firstName', $event.target.value)"
  />
  <input
    type="text"
    :value="lastName"
    @input="$emit('update:lastName', $event.target.value)"
  />
</template>