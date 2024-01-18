<script lang="ts">
import { defineComponent } from "vue";
import ChildDefineComponent from "./ChildDefineComponent.vue";

interface Member {
  id: number;
  name: string;
}

export default defineComponent({
  // 需要启用子组件作为模板
  components: {
    ChildDefineComponent,
  },

  // 定义一些数据并 `return` 给 `<template />` 用
  setup() {
    const userInfo: Member = {
      id: 1,
      name: "Petter",
    };

    // 不要忘记 `return` ，否则 `<template />` 拿不到数据
    return {
      userInfo,
    };
  },
});
</script>

<template>
  <ChildDefineComponent
    title="用户信息"
    :index="1"
    :uid="userInfo.id"
    :user-name="userInfo.name"
  />
</template>