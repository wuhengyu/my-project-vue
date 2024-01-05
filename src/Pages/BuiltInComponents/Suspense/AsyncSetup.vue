<template>
  <Suspense>
    <template #default>
      <div v-if="isLoading">Loading...</div>
      <div v-else>
        {{ posts }}
      </div>
    </template>
    <template #fallback>
      <div>Loading posts...</div>
    </template>
  </Suspense>
</template>

<script setup>
import { ref, onMounted, Suspense } from "vue";

const posts = ref(null);
const isLoading = ref(true);

onMounted(async () => {
  try {
    const res = await fetch(""); // 替换为实际的 API URL
    const data = await res.json();
    posts.value = data;
    isLoading.value = false;
  } catch (error) {
    console.error("Failed to fetch posts:", error);
  }
});
</script>