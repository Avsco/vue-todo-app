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
  <!-- <todoListOptions /> -->
</template>

<script>
import { inject, provide } from "vue";
import todoItem from "./todoItem.vue";
// import todoListOptions from "./todoListOptions.vue";

export default {
  name: "todoList",
  components: {
    todoItem
    // todoListOptions
  },

  setup() {
    provide("option", "all");
    // let todoList = inject("todos");

    function deleteTodo(id) {
      todoList.value = todoList.value.filter(todo => todo.id !== id);
    }

    function completeTodo(id) {
      todoList.value = todoList.value.map(todo => {
        if (todo.id === id) todo.status = !todo.status;
        return todo;
      });
    }

    return { todoList, completeTodo, deleteTodo };
  }
};
</script>

<style scoped lang="scss"></style>
