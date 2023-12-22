<template>
  <div>
    <BaseLayout>
      <template #header>
        <p>This is the header content</p>
      </template>
      <p>This is the main content</p>
      <template #footer>
        <p>This is the footer content</p>
      </template>
    </BaseLayout>
  </div>

  <!-- <BaseLayout>
  <template v-slot:header> 为具名插槽传入内容简写或者使用#  </template>
  </BaseLayout> -->
</template>


<script setup>
import BaseLayout from "./BaseLayout.vue";
</script>
