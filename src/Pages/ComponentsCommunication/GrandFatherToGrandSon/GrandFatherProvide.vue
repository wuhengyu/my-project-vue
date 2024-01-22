<template>
  <div><GrandSonInject /></div>
</template>

<script lang="ts">
import { defineComponent, provide, ref } from "vue";
import GrandSonInject from "./GrandSonInject.vue";

export default defineComponent({
  components: {
    GrandSonInject,
  },
  setup() {
    // 声明一个响应性变量并 provide 其自身
    // 孙组件获取后可以保持响应性
    const msg = ref("Hello World!");
    provide("msg", msg);

    // 只 provide 响应式变量的值
    // 孙组件获取后只会得到当前的值
    provide("msgValue", msg.value);

    // 声明一个方法并 provide
    function printMsg() {
      console.log(msg.value);
    }
    provide("printMsg", printMsg);

    return {
      msg,
      printMsg,
    };
  },
});
</script>

<style scoped>
</style>