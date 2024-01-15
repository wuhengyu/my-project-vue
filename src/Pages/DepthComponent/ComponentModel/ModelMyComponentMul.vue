<template>
  <div>
    <input type="text" :value="firstName" @input="onFirstNameInput" />
    <input type="text" :value="lastName" @input="onLastNameInput" />
  </div>
  <!-- <input
    type="text"
    :value="firstName"
    @input="$emit('update:firstName', $event.target.value)"
  />
  <input
    type="text"
    :value="lastName"
    @input="$emit('update:lastName', $event.target.value)"
  /> -->
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
const emit = defineEmits(["update:firstName", "update:lastName"]);

const props = defineProps({
  firstName: String,
  lastName: String,
  firstNameModifiers: { default: () => ({}) },
  lastNameModifiers: { default: () => ({}) },
});

function onFirstNameInput(e) {
  let value = e.target.value;
  if (props.firstNameModifiers.capitalize) {
    value = value.charAt(0).toUpperCase() + value.slice(1);
  }
  emit("update:firstName", value);
}

function onLastNameInput(e) {
  let value = e.target.value;
  if (props.lastNameModifiers.uppercase) {
    // 首字母大写
    // value = value.charAt(0).toUpperCase() + value.slice(1);
    // 全部大写
    value = value.toUpperCase();
  }
  emit("update:lastName", value);
}
</script>