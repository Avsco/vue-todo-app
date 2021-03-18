<template>
  <form @submit.prevent="createTodo" class="form" autocomplete="off">
    <label for="todo-input"></label>
    <input
      id="todo-input"
      v-model.trim="todo"
      type="text"
      placeholder="Create a new todo..."
      autofocus
      class="form__input"
    />
    <span v-if="todo" class="form__clear" @click="clearInput" />
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

<style scoped lang="scss">
.form {
  margin-top: 2rem;
  width: 100%;
  height: 4rem;
  padding: 20px;
  border-radius: var(--border-radius);
  background-color: var(--primary-color);

  &__input,
  &__clear {
    height: 100%;
    color: var(--color);
  }

  &__input {
    margin: 0;
    width: calc(100% - 3rem);

    font-size: 1rem;

    background-color: transparent;
    outline: none;
    border: none;
  }

  &__clear {
    display: inline-block;
    text-align: center;
    width: 3rem;

    &:after {
      content: "\274c";
    }
  }
}
</style>
