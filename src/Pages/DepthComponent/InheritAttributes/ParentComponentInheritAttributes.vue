<!-- 父组件 -->
<template>
  <div>
    <!-- 父组件向子组件传递props和attributes -->
    <ChildComponentInheritAttributes
      id="custom-id"
      class="parent-class"
      customAttr="passed-from-parent"
      :importantProp="parentData"
      @click="handleClick"
    />
  </div>
</template>

<script>
import ChildComponentInheritAttributes from "./ChildComponentInheritAttributes.vue";

export default {
  components: {
    ChildComponentInheritAttributes,
  },
  data() {
    return {
      parentData: "数据来自父组件",
    };
  },
  methods: {
    handleClick() {
      console.log("Clicked from parent");
    },
  },
};
</script>