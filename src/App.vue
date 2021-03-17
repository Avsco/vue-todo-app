<template>
  <main>
    <h1>TODO LIST</h1>
    <todo-form />
    <todo-list />
  </main>
</template>

<script>
import todoForm from "./components/todoForm.vue";
import todoList from "./components/todoList.vue";
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

    return { todos };
  }
};
</script>

<style lang="scss"></style>
