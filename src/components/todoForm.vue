<template>
  <form @submit.prevent="createTodo">
    <label for="todo-input"></label>
    <input
      id="todo-input"
      v-model.trim="todo"
      type="text"
      placeholder="Create a new todo..."
    />
    <span @click="clearInput">X</span>
  </form>
</template>

<script>
import { ref, inject } from "vue";

export default {
  name: "todoForm",
  setup() {
    let todo = ref("");
    const todos = inject("todos");

    function clearInput() {
      todo.value = "";
    }

    function createTodo() {
      try {
        if (todo.value === "") throw new Error("The form must have content");

        todos.value.push({
          id: Date.now(),
          todo: todo.value,
          status: false
        });
        clearInput();
      } catch ({ message }) {
        console.log(message);
      }
    }

    return { todo, clearInput, createTodo };
  }
};
</script>

<style scoped lang="scss"></style>
