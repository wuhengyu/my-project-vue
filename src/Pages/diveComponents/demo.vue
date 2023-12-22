<template>
  <div class="footer" :class="{ footerBottom, footerFixed }" ref="footer">
    <p class="icp">鲁ICP备202128790号</p>
  </div>
</template>

<script setup lang="tsx">
import { ref, onMounted } from "vue";
const footer = ref();
const footerBottom = ref(false);
const footerFixed = ref(false);
const documentHeight = ref();
const clientHeight = ref();
onMounted(() => {
  documentHeight.value = document.body.clientHeight;
  clientHeight.value = window.innerHeight;
  window.addEventListener(
    "resize",
    () => (clientHeight.value = window.innerHeight)
  );
});
watch(
  () => clientHeight.value,
  (value, oldValue) => {
    if (!oldvalue) {
      if (value > documentHeight) {
      } else {
      }
    }
  }
);
const footerStatus = (status: "footerBottom" | "footerFixed") => {
  if (status === "footerBottom") {
    return {
      position: "fixed",
      bottom: 0,
      left: 0,
      right: 0,
      zIndex: 100,
    };
  } else if (status === "footerFixed") {
    return {
      position: "fixed",
      bottom: 0,
      left: 0,
      right: 0,
    };
  }
};
</script>