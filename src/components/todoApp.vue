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
  name: "App",
  components: {
    todoForm,
    todoList
  },

  setup() {
    const todos = ref([]);
    provide("todos", todos);
  }
};
</script>

<style scoped lang="scss"></style>
