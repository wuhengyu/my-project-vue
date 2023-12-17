<script setup>
</script>

<template>
  <input :value="text" @input="(event) => (text = event.target.value)" />
  <input v-model="text" />

  <!-- 文本 -->
  <p>Message is: {{ message }}</p>
  <input v-model="message" placeholder="edit me" />

  <!-- 多行文本 -->
  <span>Multiline message is:</span>
  <p style="white-space: pre-line">{{ message }}</p>
  <textarea v-model="message" placeholder="add multiple lines"></textarea>
</template>