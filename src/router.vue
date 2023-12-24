<script setup>
import { ref, computed } from "vue";
import Home from "./Pages/Home.vue";
import About from "./Pages/About.vue";
import NotFound from "./Pages/NotFound.vue";
import App from "./Pages/Foundation/App.vue";
import calculate from "./Pages/Foundation/calculate.vue";
import slot from "./Pages/diveComponents/slot.vue";
import BaseLayout from "./Pages/diveComponents/BaseLayout.vue";
import namedSlot from "./Pages/diveComponents/namedSlot.vue";
import componentEvents from "./Pages/diveComponents/componentEvents.vue";
import eventParametersVue from "./Pages/diveComponents/eventParameters.vue";
import componentVModel from "./Pages/diveComponents/component-v-model.vue";
import componentBasics from "./Pages/diveComponents/basics/oneComponent.vue";
import noBuildSteps from "./Pages/diveComponents/basics/noBuildSteps.vue";
import UseComponents from "./Pages/diveComponents/basics/UseComponents.vue";
import PassProps from "./Pages/diveComponents/basics/PassProps.vue";

const routes = {
  "/Home": Home,
  "/about": About,
  "/App": App,
  "/calculate": calculate,
  "/non-existent-path": NotFound,
  "/slot": slot,
  "/namedSlot": namedSlot,
  "/BaseLayout": BaseLayout,
  "/componentEvents": componentEvents,
  "/eventParameters": eventParametersVue,
  "/component-v-model": componentVModel,
  "/componentBasics": componentBasics,
  "/noBuildSteps": noBuildSteps,
  "/UseComponents": UseComponents,
  "/PassProps": PassProps,
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
  <a href="#/non-existent-path">NotFound</a> | <a href="#/slot">slot</a> |
  <a href="#/BaseLayout">BaseLayout</a> | <a href="#/namedSlot">namedSlot</a> |
  <a href="#/componentEvents">componentEvents</a> |
  <a href="#/eventParameters">eventParameters</a> |
  <a href="#/component-v-model">component-v-model</a> |
  <a href="#/componentBasics">componentBasics</a> |
  <a href="#/noBuildSteps">noBuildSteps</a> |
  <a href="#/UseComponents">UseComponents</a> |
  <a href="#/PassProps">PassProps</a>
  <component :is="currentView" />
</template>