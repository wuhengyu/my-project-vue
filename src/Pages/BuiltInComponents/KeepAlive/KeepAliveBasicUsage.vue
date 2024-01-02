<script setup>
import { shallowRef } from "vue";
import CompA from "./CompA.vue";
import CompB from "./CompB.vue";

const current = shallowRef(CompA);
</script>

<template>
  <h3>KeepAlive 基础使用</h3>
  <div class="demo">
    <label><input type="radio" v-model="current" :value="CompA" /> A</label>
    <label><input type="radio" v-model="current" :value="CompB" /> B</label>
    <KeepAlive>
      <component :is="current"></component>
    </KeepAlive>
  </div>
</template>