<template>
  <ChildModel
    v-model:uid="userInfo.id"
    v-model:username="userInfo.name"
    v-model:age="userInfo.age"
  />
</template>

<script lang="ts">
import ChildModel from "./ChildModel.vue";
import { defineComponent, reactive } from "vue";

// 定义了一个类型为Member的接口，描述了用户信息对象结构，包含id（数字类型）和name（字符串类型）两个属性
interface Member {
  id: number;
  name: string;
}

export default defineComponent({
  // 需要启用子组件作为模板
  // 注册了ChildDefineComponent，这样在组件模板中就可以使用这个子组件。
  components: {
    ChildModel,
  },

  // 定义一些数据并 `return` 给 `<template />` 用
  // 用于设置组件的响应式状态和计算属性
  setup() {
    // 初始化了一个符合Member类型的常量userInfo，其中存储了一个具体用户的ID和姓名
    // 1.定义并使用数据类型的接口
    const userInfo: Member = reactive({
      id: 1,
      name: "Peter",
    });
    return {
      userInfo,
    };
  },
});
</script>

<style lang="scss" scoped>
</style>