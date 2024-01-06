<template>
  <div>
    <Inhert-Attributes-Parent-Component
      class="container"
      style="background-color: rgb(167, 212, 175)"
    >
      <template v-slot:default> Hello, InhertAttributesApplication!</template>
    </Inhert-Attributes-Parent-Component>
  </div>
</template>

<script>
import InhertAttributesParentComponent from "./InhertAttributesParentComponent.vue";

export default {
  components: {
    InhertAttributesParentComponent,
  },
};
</script>