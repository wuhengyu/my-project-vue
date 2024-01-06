<template>
  <div>
    <!-- 定义 handleClick 方法，并在其中处理点击事件的逻辑 -->
    <button @click="handleClick" class="fancy-btn">点击我触发事件</button>
  </div>
  <div>
    <!-- 通过 $emit 方法来触发一个名为 someEvent 的自定义事件，
      并传递一个字符串 'to make each day count!' 作为事件的 payload（数据） -->
    <!-- 子组件内部直接触发事件，将事件传递给父组件或其他监听了该事件的组件。
    父组件可以通过 @someEvent 来监听该事件，并在触发时执行相应的回调函数。 -->
    <button @click="$emit('someEvent', 'to make each day count!')">
      click me
    </button>
  </div>
</template>

<!-- <button @click="handleClick" class="fancy-btn">点击我触发事件</button>
<button @click="$emit('someEvent', 'to make each day count!')">click me</button>
第一种方式使用自定义方法作为点击事件的处理函数，可以在方法内部处理自定义逻辑。
第二种方式直接通过 $emit 方法触发自定义事件，并在组件外部监听该事件。这种方式更方便，适用于简单的事件触发和数据传递。 -->

<script>
export default {
  methods: {
    handleClick() {
      // 在这里触发事件并传递数据
      this.$emit("some-event", "Hello, World!");
    },
  },
};
</script>

<style scoped>
/* 可选的样式规则 */
.fancy-btn {
  color: #fff;
  background: linear-gradient(315deg, #1135d3 25%, #ff64c4);
  border: none;
  padding: 5px 10px;
  margin: 5px;
  border-radius: 8px;
  cursor: pointer;
}
</style>