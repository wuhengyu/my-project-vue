<template>
  <div>
    <h2>父组件Parent Component</h2>
    <h2 style="color: rgb(157, 103, 228)">
      <slot />
    </h2>
    <Inhert-Attributes-Child-Component v-bind="$attrs" />
  </div>
</template>

<script>
import InhertAttributesChildComponent from "./InhertAttributesChildComponent.vue";

export default {
  components: {
    InhertAttributesChildComponent,
  },
};
</script>