<template>
  <div>{{ msg }}</div>
</template>

<script lang="ts">
import { defineComponent, inject } from "vue";
import type { Ref } from "vue";

export default defineComponent({
  setup() {
    // 获取响应式变量
    const msg = inject<Ref<string>>("msg");
    console.log(msg!.value);

    // 获取普通的字符串
    const msgValue = inject<string>("msgValue");
    console.log(msgValue);

    // 获取函数
    const printMsg = inject<() => void>("printMsg");
    if (typeof printMsg === "function") {
      printMsg();
    }
    return { msg, printMsg };
  },
});
</script>

<style scoped>
</style>