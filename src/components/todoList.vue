<template>
  <ul>
    <todo-item
      v-for="value in listTodoOptions"
      :key="value.id"
      :todo="value"
      @todo-complete="completeTodo($event)"
      @todo-delete="deleteTodo($event)"
    />
  </ul>
  <div>
    <span>{{ listTodoOptions.length }}</span>
    <todoListOptions />
  </div>
</template>

<script>
import { computed, inject, provide, ref } from "vue";
import todoItem from "./todoItem.vue";
import todoListOptions from "./todoListOptions.vue";

export default {
  name: "todoList",
  components: {
    todoItem,
    todoListOptions
  },

  setup() {
    let todoOption = ref("all");
    let todoList = inject("todos");
    provide("showTodo", todoOption);

    const listTodoOptions = computed(() => {
      if (todoOption.value === "all") return todoList.value;
      if (todoOption.value === "active")
        return todoList.value.filter(todo => !todo.status);
      if (todoOption.value === "completed")
        return todoList.value.filter(todo => todo.status);
      return todoList.value;
    });

    function deleteTodo(id) {
      todoList.value = todoList.value.filter(todo => todo.id !== id);
    }

    function completeTodo(id) {
      todoList.value = todoList.value.map(todo => {
        if (todo.id === id) todo.status = !todo.status;
        return todo;
      });
    }

    return { listTodoOptions, completeTodo, deleteTodo };
  }
};
</script>

<style scoped lang="scss"></style>
