<template>
  <ChildModel
    v-model:uid="userInfo.id"
    v-model:username="userInfo.name"
    v-model:age="userInfo.age"
  />
</template>

<script lang="ts">
import ChildModel from "./ChildModel.vue";
import { defineComponent, reactive } from "vue";

interface Member {
  id: number;
  name: string;
  age: number;
}

export default defineComponent({
  components: {
    ChildModel,
  },
  setup() {
    const userInfo: Member = reactive({
      id: 1,
      name: "Petter",
      age: 25,
    });
    return {
      userInfo,
    };
  },
});
</script>

<style lang="scss" scoped>
</style>