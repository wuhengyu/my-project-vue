<template>
  <h1>文本</h1>
  <p>Message is: {{ message }}</p>
  <input v-model="message" placeholder="edit me" />

  <h1>多行文本</h1>
  <span>Multiline message is:</span>
  <p style="white-space: pre-line">{{ message }}</p>
  <textarea v-model="message" placeholder="add multiple lines"></textarea>

  <h1>复选框</h1>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">{{ checked }}</label>

  <h1>多个复选框</h1>
  <div>Checked names: {{ checkedNames }}</div>
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
  <label for="jack">Jack</label>
  <input type="checkbox" id="john" value="John" v-model="checkedNames" />
  <label for="john">John</label>
  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
  <label for="mike">Mike</label>

  <h1>单选按钮</h1>
  <div>Picked: {{ picked }}</div>
  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>
  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>

  <h1>选择器</h1>
  <div>Selected: {{ selected }}</div>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>

  <h1>值绑定</h1>
  <!-- `picked` 在被选择时是字符串 "a" -->
  <input type="radio" v-model="picked" value="a" />
  <!-- `toggle` 只会为 true 或 false -->
  <input type="checkbox" v-model="toggle" />
  <!-- `selected` 在第一项被选中时为字符串 "abc" -->
  <select v-model="selected">
    <option value="abc">ABC</option>
  </select>
  <h3>复选框</h3>
  <input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />
  <input
    type="checkbox"
    v-model="toggle"
    :true-value="dynamicTrueValue"
    :false-value="dynamicFalseValue"
  />
  <h3>单选按钮</h3>
  <input type="radio" v-model="pick" :value="first" />
  <input type="radio" v-model="pick" :value="second" />
  <h3>选择器选项</h3>
  <select v-model="selected">
    <!-- 内联对象字面量 -->
    <option :value="{ number: 123 }">123</option>
  </select>

  <h1>修饰符</h1>
  <!-- 在 "change" 事件后同步更新而不是 "input" -->
  <input v-model.lazy="msg" />
  <input v-model.number="age" />
</template>

<script setup>
import { ref } from "vue";
const message = ref("");
const picked = ref("");
const toggle = ref(false);
const selected = ref("");
const first = ref("");
const second = ref("");
const dynamicTrueValue = ref("foo");
const dynamicFalseValue = ref("bar");
const pick = ref("");
const msg = ref("");
const age = ref("");
const checkedNames = ref([]);
const checked = ref(true);
</script>