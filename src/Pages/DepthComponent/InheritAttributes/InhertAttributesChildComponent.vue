<template>
  <div v-bind="$attrs">
    <h3>子组件InhertAttributesChildComponent</h3>
    <input />
    <input v-bind="$attrs" />
    <p>
      即使将 inheritAttrs 设置为 true，子组件也不会直接继承父组件的非 prop
      属性到子组件的根元素上。
    </p>
    <p v-bind="$attrs">
      使用了 $attrs 对象来继承属性。通过 v-bind="$attrs" 将 $attrs
      对象中的属性绑定到输入框上。
      这样，子组件将显示继承的属性，包括样式、类名、事件监听器等。父组件中传递给子组件的属性将被应用到子组件的输入框上。
      请注意，inheritAttrs: false 的配置告诉 Vue 不要自动将根元素的非 prop
      属性绑定到组件的根元素上。 这样可以避免重复绑定属性。
    </p>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
};
</script>