<script setup>
import FancyButton from "./FancyButton.vue";
import AwesomeIcon from "./AwesomeIcon.vue";
</script>

<template>
  <br />
  <FancyButton> Click me </FancyButton>
  <FancyButton>
    <span style="color: cyan">Click me! </span>
    <AwesomeIcon />
  </FancyButton>
</template>