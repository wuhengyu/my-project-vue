<template>
  <AttributeMyButton class="ParentClass" @myclick="handleClick" />
</template>

<script setup>
import AttributeMyButton from "./AttributeMyButton.vue";

const handleClick = (n) => {
  console.log("Parent handleClick, " + n);
};
</script>

<style>
.large {
  font-size: 20px;
  color: rosybrown;
  background: rgb(175, 241, 149);
}
</style>