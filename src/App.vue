<template>
  <main>
    <h1>TODO LIST</h1>
    <todo-form @submit-todo="createTodo($event)" />
  </main>
</template>

<script>
import todoForm from "./components/todoForm.vue";

export default {
  name: "App",
  components: {
    todoForm
  },

  setup() {
    function createTodo(todo) {
      console.log(todo);
    }

    return { createTodo };
  }
};
</script>

<style lang="scss"></style>
