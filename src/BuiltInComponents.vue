<script setup>
import { ref, computed } from "vue";
import Transition from "./Pages/BuiltInComponents/Transition/Transition.vue";
import NotFound from "./Pages/NotFound.vue";

const routes = {
  "/non-existent-path": NotFound,
  "/Transition": Transition,
};
const currentPath = ref(window.location.hash);
window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});
const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"] || NotFound;
});
</script>
<template>
  <h1>内置组件</h1>
  <a href="#/Transition">Transition</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |
  <component :is="currentView" />
</template>