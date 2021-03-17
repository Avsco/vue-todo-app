<template>
  <ul>
    <todo-item
      v-for="value in todoList"
      :key="value.id"
      :todo="value"
      @todo-complete="completeTodo($event)"
      @todo-delete="deleteTodo($event)"
    />
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

    function deleteTodo(id) {
      console.log(id);
    }

    function completeTodo(id) {
      console.log(id);
    }

    return { todoList, completeTodo, deleteTodo };
  }
};
</script>

<style scoped lang="scss"></style>
