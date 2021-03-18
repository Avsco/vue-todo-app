<template>
  <button @click="showTodos('all')">All</button>
  <button @click="showTodos('active')">Active</button>
  <button @click="showTodos('completed')">Completed</button>
</template>

<script>
import { inject } from "@vue/runtime-core";

export default {
  name: "todoOptions",
  setup() {
    let option = inject("showTodo");

    function showTodos(typeTodo) {
      option.value = typeTodo;
    }

    return { showTodos };
  }
};
</script>

<style scoped lang="scss"></style>
