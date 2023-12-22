<template>
  <div class="container">
    <header style="font-size: 30px; color: rgb(13, 216, 97)">
      <slot name="header"></slot>
    </header>
    <main style="font-size: 40px; color: rgb(205, 240, 7)">
      <slot></slot>
    </main>
    <footer style="font-size: 20px; color: aqua">
      <slot name="footer"></slot>
    </footer>
  </div>
</template>
<script setup>
</script>