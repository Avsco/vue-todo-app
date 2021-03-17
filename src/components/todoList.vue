<template>
  <ul>
    <todo-item v-for="value in todoList" :key="value.id" :todo="value" />
  </ul>
</template>

<script>
import { inject } from "vue";
import todoItem from "./todoItem.vue";

export default {
  name: "todoList",
  components: {
    todoItem
  },

  setup() {
    const todoList = inject("todos");

    return { todoList };
  }
};
</script>

<style scoped lang="scss"></style>
