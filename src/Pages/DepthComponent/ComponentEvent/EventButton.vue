<template>
  <!-- 当用户点击这个按钮时，会触发一个自定义事件，并且附带传递一个参数 -->
  <!-- 触发名为 'increaseBy' 的事件，并向父组件传递字符串 '传递的payload（数据）' 作为该事件的参数 -->
  <!-- 父组件可以通过在其模板中监听此事件并提供相应的处理函数来响应这个动作 -->
  <button @click="$emit('increaseBy', '传递的payload（数据）')">
    Increase by 1
  </button>
</template>