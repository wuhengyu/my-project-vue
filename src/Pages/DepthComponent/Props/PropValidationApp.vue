<template>
  <!-- 字面值（如字符串、数字、布尔值等），我们可以直接将它们作为静态值传递给组件的属性，而无需使用属性绑定 -->
  <div>
    <PropValidation
      propA="123"
      :propB="456"
      propC="Hello World"
      :propD="200"
      :propE="{ message: 'Hi' }"
      propF="success"
      :propG="customFunction"
    />
  </div>
</template>

<script>
import PropValidation from "./PropValidation.vue";

export default {
  components: {
    PropValidation,
  },
};
</script>