<template>
  <OnChildAttributesInherit
    :class="myClass"
    :style="myStyle"
    @myEvent="handleEvent"
    name="张三"
  />
</template>

<script setup>
import OnChildAttributesInherit from "./OnChildAttributesInherit.vue";

const myClass = "parentClass";
const myStyle = {
  color: "red",
};

const handleEvent = (e) => {
  console.log("Event received:", e);
};
</script>