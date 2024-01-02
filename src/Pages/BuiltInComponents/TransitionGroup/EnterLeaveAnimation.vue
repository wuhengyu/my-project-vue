<template>
  <h3>进入/离开动画</h3>
  <button @click="insert">插入</button>
  <br /><br /><br />
  <button @click="shuffle">洗牌</button>
  <br /><br /><br />
  <button @click="reset">重置</button>
  <br /><br /><br />
  <button @click="randomRemove">删除</button>
  <br /><br /><br />
  <TransitionGroup tag="ul" name="fade" class="container">
    <div v-for="item in items" class="item" :key="item">
      {{ item }}
      <button @click="remove(item)">x</button>
    </div>
  </TransitionGroup>
</template>

<script setup>
import { shuffle as _shuffle } from "lodash-es";
import { ref } from "vue";

const getInitialItems = () => [1, 2, 3, 4, 5];
const items = ref(getInitialItems());
let id = items.value.length + 1;

function insert() {
  const i = Math.round(Math.random() * items.value.length);
  items.value.splice(i, 0, id++);
}

function reset() {
  items.value = getInitialItems();
}

function shuffle() {
  items.value = _shuffle(items.value);
}

function remove(item) {
  const i = items.value.indexOf(item);
  if (i > -1) {
    items.value.splice(i, 1);
  }
}

function randomRemove() {
  if (items.value.length > 0) {
    const i = Math.floor(Math.random() * items.value.length);
    items.value.splice(i, 1);
  } else {
    alert("No items to remove");
  }
}
</script>

<style>
.container {
  position: relative;
  padding: 0;
}

.item {
  width: 100%;
  height: 30px;
  background-color: #f3f3f3;
  border: 1px solid #666;
  box-sizing: border-box;
}

/* 1. 声明过渡效果 */
.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

/* 2. 声明进入和离开的状态 */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}

/* 3. 确保离开的项目被移除出了布局流
      以便正确地计算移动时的动画效果。 */
.fade-leave-active {
  position: absolute;
}
</style>