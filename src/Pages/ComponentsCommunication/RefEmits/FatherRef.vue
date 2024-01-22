<template>
  <ChildRef
    ref="child"
    v-model:uid="userInfo.id"
    v-model:username="userInfo.name"
    v-model:age="userInfo.age"
  />
</template>

<script lang="ts">
import { defineComponent, onMounted, ref, reactive } from "vue";
import ChildRef from "./ChildRef.vue";

interface Member {
  id: number;
  name: string;
  age: number;
}

export default defineComponent({
  components: {
    ChildRef,
  },
  setup() {
    const userInfo: Member = reactive({
      id: 1,
      name: "Petter",
      age: 25,
    });

    // 指定了 child 的类型为 ChildRef 组件的实例类型
    // child 变量只能引用 ChildRef 组件的实例，不能引用其他类型的值
    // 表示child变量将会持有ChildRef组件的具体实例对象
    const child = ref<InstanceType<typeof ChildRef>>();

    // 或者
    // 这种声明方式没有指定泛型类型，它会根据初始化的值进行类型推断
    // child 的类型将是一个 Ref 对象，可以引用任何类型的值
    // const child = ref();

    // 请保证视图渲染完毕后再执行操作
    // 当组件挂载并完成视图渲染后执行其回调函数
    // onMounted是Vue生命周期钩子之一
    onMounted(async () => {
      // 执行子组件里面的 AJAX 请求函数
      // 使用.value属性访问到child引用对应的子组件实例
      // 异步AJAX请求函数，用于获取数据列表
      await child.value!.queryList();

      // 显示子组件里面的弹窗
      // ! 符号在这里是 TypeScript 中的非空断言操作符。它表示我们确定 child.value 不为空，并且可以安全地访问其属性和方法。
      // 如果 child.value 为 null 或 undefined，则会引发运行时错误
      // 在使用 ! 时，请确保您已经确认了该值的非空性，并且可以安全地进行访问
      child.value!.isShowDialog = true;

      // 先弹窗再隐藏
      await child.value!.handleDialogClose();
    });

    // 必须 `return` 出去才可以给到 `<template />` 使用
    return {
      child,
      userInfo,
    };
  },
});
</script>

<style lang="scss" scoped>
</style>