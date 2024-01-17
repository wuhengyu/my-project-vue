<template>
  <h3>父组件传递数据给子组件</h3>
  <div>
    <!-- 单向数据绑定语法，通过v-bind或其简写:来将父组件的数据属性parentMessage传递给子组件的一个名为message的prop（属性）。
    这意味着当parentMessage的值发生变化时，子组件接收到的message也会同步更新 -->
    <props-child-component :message="parentMessage" />
    <!-- 直接为子组件的message prop指定了一个固定的字符串值"hahahahahaha"。与第一种方式不同，这种方式传递的值是静态的，不会随父组件状态变化而变化。 -->
    <props-child-component message="hahahahahaha" />
    <!-- 与第一个类似，使用了v-bind指令的完整语法来绑定message prop到父组件的数据属性heieheiehei，效果与第一种写法等同，
    即实现了动态数据绑定，当父组件的heieheiehei属性值改变时，该子组件的message prop也将同步更新。 -->
    <props-child-component v-bind:message="heieheiehei" />
  </div>
</template>

<!-- <script>
import PropsChildComponent from "./PropsChildComponent.vue";

export default {
  components: {
    PropsChildComponent,
  },
  data() {
    return {
      parentMessage: "Hello from parent component",
    };
  },
};
</script> -->

<script setup>
import PropsChildComponent from "./PropsChildComponent.vue";
const parentMessage = "Hello from parent component";
</script>