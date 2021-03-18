<template>
  <section class="todo">
    <h1 class="todo__title">TODO</h1>
    <todo-form />
    <todo-list />
  </section>
</template>

<script>
import todoForm from "./todoForm.vue";
import todoList from "./todoList.vue";
import { ref, provide } from "vue";

export default {
  name: "todoApp",
  components: {
    todoForm,
    todoList
  },

  setup() {
    let todos = ref([]);
    provide("todos", todos);
  }
};
</script>

<style scoped lang="scss">
.todo {
  margin-top: 5rem;
  width: 76vw;
}

.todo__title {
  color: white;
  font-weight: 700;
  font-size: 2rem;
}
</style>
