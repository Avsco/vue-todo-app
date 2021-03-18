<template>
  <h1>TODO LIST</h1>
  <todo-form />
  <todo-list />
</template>

<script>
import todoForm from "./todoForm.vue";
import todoList from "./todoList.vue";
import { ref, provide } from "vue";

export default {
  name: "todoApp",
  components: {
    todoForm,
    todoList
  },

  setup() {
    let todos = ref([]);
    provide("todos", todos);
  }
};
</script>

<style scoped lang="scss"></style>
