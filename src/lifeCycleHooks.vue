<script setup>
import { onMounted } from "vue";

onMounted(() => {
  console.log(`the component is now mounted.`);
});

setTimeout(() => {
  onMounted(() => {
    // 异步注册时当前组件实例已丢失
    // 这将不会正常工作
  });
}, 100);
</script>