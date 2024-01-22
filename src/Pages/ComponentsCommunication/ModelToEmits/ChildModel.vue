<template>
  <div>
    <p>UID: {{ uid }}</p>
    <p>Username: {{ username }}</p>
    <p>Age: {{ age }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from "vue";

export default defineComponent({
  props: {
    uid: Number,
    username: String,
    age: Number,
  },
  // 定义了三个事件发射器（emits），分别对应更新上述props的值
  emits: ["update:uid", "update:username", "update:age"],

  // setup 函数是组件的入口点，它返回一个包含状态、计算属性、方法和生命周期钩子等的对象
  // setup(_, { emit }) 是 Vue 3 中的 Composition API 方法, 用于组件的初始化逻辑。
  // 参数中的 _ 表示没有使用props，而 emit 则是用于触发事件的方法。
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
  },
});
</script>

<!-- 使用 props / emits ，如果要更新父组件的数据，还需要在父组件声明一个更新函数并绑定事件给子组件，才能够更新。
而使用 v-model / emits ，无需在父组件声明更新函数，只需要在子组件里通过 update: 前缀加上 v-model 的属性名这样的格式，
即可直接定义一个更新事件。 -->
