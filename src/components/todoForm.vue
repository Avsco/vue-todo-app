<template>
  <form @submit.prevent="createTodo">
    <input v-model.trim="todo" type="text" placeholder="Create a new todo..." />
    <span @click="clearInput">X</span>
  </form>
</template>

<script>
import { ref } from "vue";

export default {
  name: "todoForm",
  emits: ["submitTodo"],
  setup(_, { emit }) {
    let todo = ref("");

    function clearInput() {
      todo.value = "";
    }

    function createTodo() {
      try {
        if (todo.value === "") throw new Error("The form must have content");

        // emit("submitTodo", todo.value);
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
