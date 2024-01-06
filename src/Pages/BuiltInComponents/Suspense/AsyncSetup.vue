<template>
  <h3>AsyncSetup</h3>
  <Suspense>
    <template #default>
      <!-- 默认模板 -->
      <div v-if="isLoading">Loading...</div>
      <!-- 加载过程中显示加载中的提示 -->
      <div v-else>
        {{ posts }}
      </div>
      <!-- 显示 posts 值 -->
    </template>
    <template #fallback>
      <!-- 背景模板 -->
      <div>Loading posts...</div>
      <!-- 加载帖子中... -->
    </template>
  </Suspense>
</template>

<script setup>
import { ref, onMounted, Suspense } from "vue";

// 使用 ref 创建(posts, isLoading)两个响应式变量
const posts = ref(null);
const isLoading = ref(true);

// 在页面加载时调用该函数，异步获取数据并更新 posts 和 isLoading 的值
onMounted(async () => {
  try {
    const res = await fetch("https://www.httpbin.org/get"); // 替换为实际的 API URL
    const data = await res.json();
    posts.value = data; // 更新 posts 值
    isLoading.value = false; // 更新 isLoading 值为 false
  } catch (error) {
    console.error("Failed to fetch posts:", error);
  }
});
</script>