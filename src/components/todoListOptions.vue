<template>
  <article class="options">
    <button
      v-for="value in options"
      :key="value"
      :class="
        `options__button ${option === value ? 'options__button--selected' : ''}`
      "
      @click="showTodos(value)"
    >
      {{ value }}
    </button>
  </article>
</template>

<script>
import { inject, shallowRef } from "@vue/runtime-core";

export default {
  name: "todoOptions",
  setup() {
    let option = inject("showTodo");
    let options = shallowRef(["all", "active", "completed"]);

    function showTodos(typeTodo) {
      option.value = typeTodo;
    }

    return { showTodos, options, option };
  }
};
</script>

<style scoped lang="scss">
.options {
  padding-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;

  @media (min-width: 410px) {
    flex-direction: row;
  }

  @media (min-width: 680px) {
    padding-top: 0;
  }

  &__button {
    padding: 10px;
    padding-left: 15px;
    padding-right: 15px;
    margin: 10px;
    width: 120px;

    background-color: transparent;
    border: 2px solid var(--secondary-color);
    background-repeat: var(--border-radius);
    color: var(--secondary-color);
    font-weight: 700;
    text-transform: capitalize;
    outline: none;

    @media (min-width: 680px) {
      all: unset;
      font-weight: 700;
      margin-left: 10px;
      margin-right: 10px;
      text-transform: capitalize;
      font-family: "Comic Sans MS", Courier, monospace;
    }

    &--selected {
      color: white;
      background-color: var(--secondary-color);

      @media (min-width: 680px) {
        all: unset;
        font-weight: 700;
        margin-left: 10px;
        margin-right: 10px;
        color: var(--secondary-color);
        text-transform: capitalize;
        font-family: "Comic Sans MS", Courier, monospace;
      }
    }
  }
}
</style>
