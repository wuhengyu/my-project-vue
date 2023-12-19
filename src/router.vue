<script setup>
import { ref, computed } from "vue";
import Home from "./Pages/Home.vue";
import About from "./Pages/About.vue";
import NotFound from "./Pages/NotFound.vue";
import App from "./Pages/Foundation/App.vue";
import calculate from "./Pages/Foundation/calculate.vue";
import slot from "./Pages/diveComponents/slot.vue";
const routes = {
  "/": Home,
  "/about": About,
  "/App": App,
  "/calculate": calculate,
  "/non-existent-path": NotFound,
  "/slot": slot,
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
  <a href="#/">Home</a> | <a href="#/about">About</a> |
  <a href="#/App">App</a> | <a href="#/calculate">calculate</a> |
  <a href="#/non-existent-path">NotFound</a> | <a href="#/slot">slot</a>
  <component :is="currentView" />
</template>