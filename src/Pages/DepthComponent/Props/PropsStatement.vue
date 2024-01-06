<script setup>
const props = defineProps(["foo"]);

console.log(props.foo);
</script>
<!-- 或者 -->
<!-- <script setup>
export default {
  props: ['foo'],
  setup(props) {
    // setup() 接收 props 作为第一个参数
    console.log(props.foo)
  }
}
</script> -->