<template>
  <div>
    <!-- 用于控制一个包含“显示弹窗内容”的<div>标签是否展示 -->
    <div v-if="isShowDialog">
      <p>显示弹窗内容</p>
    </div>
    <div>
      <p>UID: {{ uid }}</p>
      <p>Username: {{ username }}</p>
      <p>Age: {{ age }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "vue";

// 子组件通知父组件
export default defineComponent({
  props: {
    uid: Number,
    username: String,
    age: Number,
  },

  // 定义了三个事件发射器（emits），分别对应更新上述props的值
  emits: ["update:uid", "update:username", "update:age"],

  // setup函数是Vue 3中用于组件实例化前执行的钩子，它返回的对象会作为组件的上下文暴露给模板或其他组合式函数
  setup(_, { emit }) {
    // 生命周期钩子 onMounted, 在组件挂载到DOM后执行一个回调函数
    onMounted(() => {
      // 在回调函数内部设置了一个定时器，两秒（2000毫秒）后执行其内的代码
      setTimeout(() => {
        // 当定时器时间到达后，调用 emit 函数触发 update:username 事件，并传入新的用户名 "Tom" 作为参数
        // 两秒后将组件外部（通常是父组件）传递过来的 username 更新为 "Tom"
        emit("update:username", "Tom");
        emit("update:age", 2500);
        emit("update:uid", 12345);
      }, 2000);
    });

    // 创建了一个名为isShowDialog的响应式引用，初始值为true，表示初始化时弹窗是显示状态
    const isShowDialog = ref(true);

    async function queryList() {
      // 执行 AJAX 请求的逻辑
      // queryList函数是一个异步函数，模拟了执行AJAX请求的过程，这里通过setTimeout模拟耗时2秒的异步操作，并在完成后打印"查询列表完成"
      await new Promise((resolve) => setTimeout(resolve, 200)); // 模拟异步请求
      console.log("查询列表完成");
    }

    // 当调用该函数时，首先弹出一个警告框提示“关闭弹窗”，然后将isShowDialog的值设置为false，这会导致基于isShowDialog值进行条件渲染的弹窗内容隐藏
    async function handleDialogClose() {
      alert("关闭弹窗");
      isShowDialog.value = false;
    }
    // 组件通过return语句从setup函数中导出了isShowDialog、queryList和handleDialogClose这三个变量和方法，
    // 使得它们可以在模板或者其他需要响应式数据和函数的地方被访问和使用
    return {
      isShowDialog,
      queryList,
      handleDialogClose,
    };
  },
});
</script>