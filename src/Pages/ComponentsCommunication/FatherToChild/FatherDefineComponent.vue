<script lang="ts">
import { defineComponent, reactive } from "vue";
import ChildDefineComponent from "./ChildDefineComponent.vue";

// 定义了一个类型为Member的接口，描述了用户信息对象结构，包含id（数字类型）和name（字符串类型）两个属性
interface Member {
  id: number;
  name: string;
}

export default defineComponent({
  // 需要启用子组件作为模板
  // 注册了ChildDefineComponent，这样在组件模板中就可以使用这个子组件。
  components: {
    ChildDefineComponent,
  },

  // 定义一些数据并 `return` 给 `<template />` 用
  // 用于设置组件的响应式状态和计算属性
  setup() {
    // 初始化了一个符合Member类型的常量userInfo，其中存储了一个具体用户的ID和姓名
    // 1.定义并使用数据类型的接口
    const userInfo: Member = reactive({
      id: 1,
      name: "Pe",
    });
    // 2.定义并使用Props类型的接口
    // 定义一个用于Prop的接口
    // interface Props {
    //   userId: number;
    //   userName: string;
    // }

    // export default defineComponent({
    //   props: {
    //     // 使用接口约束props
    //     ...makeProps<Props>(),
    //   },

    //   setup(props: Props) {
    //     // 现在props对象会自动具有类型检查
    //     const displayUserInfo = () => console.log(`User ID: ${props.userId}, Name: ${props.userName}`);

    //     // ...
    //     return {};
    //   },
    // 3.在方法或计算属性中使用接口：
    // interface FormInput {
    //   value: string;
    //   isValid: boolean;
    // }

    // export default defineComponent({
    //   setup() {
    //     const formInput: Ref<FormInput> = ref({ value: '', isValid: false });

    //     const validateForm = (input: FormInput) => {
    //       // 输入参数会被类型检查
    //       // ...
    //     };

    //     // ...

    //     return {
    //       formInput,
    //       validateForm,
    //     };
    //   },
    // });

    // 不要忘记 `return` ，否则 `<template />` 拿不到数据
    // 使用return语句将userInfo暴露出去，使得在组件的模板中可以访问并绑定到HTML元素上
    return {
      userInfo,
    };
  },
});
</script>

<template>
  <!-- uid：通过props绑定的方式传递userInfo.id，即父组件中定义的用户ID -->
  <!-- user-name：同样通过props绑定的方式传递userInfo.name，即父组件中定义的用户名 -->
  <ChildDefineComponent
    title="用户信息"
    :index="1"
    :uid="userInfo.id"
    :user-name="userInfo.name"
  />
</template>