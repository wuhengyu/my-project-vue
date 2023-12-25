<script setup>
import { ref, reactive, computed } from "vue";

const author = reactive({
  name: "经典文学",
  books: ["老人与海", "约翰.克里斯朵夫", "麦田里的守望者"],
});

// 一个计算属性 ref
// 和function calculateBooksMessage()不同之处在于计算属性值会基于其响应式依赖被缓存
// 只要 author.books 不改变，publishedBooksMessage 都会立即返回先前的计算结果，不用重复执行 getter 函数
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? "Yes" : "No";
});

// 组件中
function calculateBooksMessage() {
  return author.books.length > 0 ? "Yes" : "No";
}

// 下面的计算属性永远不会更新，因为 Date.now() 并不是一个响应式依赖
const now = computed(() => Date.now());

// 实时计算
const now2 = ref(Date.now());
setInterval(() => {
  now2.value = Date.now(); // 更新 now 的值
}, 1000);

const currentTime = computed(() => now2.value);
</script>

<template>
  <h1>App4</h1>
  <p>名称显示：{{ author.name }} 书籍列表显示:{{ author.books }}</p>
  <span>{{ author.books.length > 0 ? "Yes" : "No" }}</span>
  <p>computed属性1</p>
  <!-- 计算属性 ref 也会在模板中自动解包，因此在模板表达式中引用时无需添加 .value -->
  <span>{{ publishedBooksMessage }}</span>
  <p>computed属性2</p>
  <p>{{ calculateBooksMessage() }}</p>

  <p>{{ now }}</p>
  <p>{{ currentTime }}</p>
</template>