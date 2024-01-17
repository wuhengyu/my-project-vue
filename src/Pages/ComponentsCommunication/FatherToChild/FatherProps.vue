<script lang="ts">
import { defineComponent } from "vue";
import ChildProps from "./ChildProps.vue";

// Member接口定义了一个成员结构，包含id（数字类型）和name（字符串类型）两个属性。
interface Member {
  id: number;
  name: string;
}

export default defineComponent({
  // 需要启用子组件作为模板
  components: {
    ChildProps,
  },

  // setup函数：这是Vue3 Composition API中的一个重要生命周期钩子，用于设置组件的响应式状态和副作用逻辑。
  // 定义一些数据并 `return` 给 `<template />` 用
  setup() {
    // 定义了一个名为userInfo的变量，它的类型为Member
    const userInfo: Member = {
      id: 1,
      name: "Petter",
    };

    // 不要忘记 `return` ，否则 `<template />` 拿不到数据
    // 通过return将userInfo暴露出去，这样在模板中就可以访问到这个变量及其所有属性。
    return {
      userInfo,
    };
  },
});

// 组合式API写法
// 定义响应式数据
// const userInfo = reactive({
//   id: 1,
//   name: "Petter",
// });
</script>

<template>
  <ChildProps
    title="用户信息"
    :index="1"
    :uid="userInfo.id"
    :user-name="userInfo.name"
  />
</template>