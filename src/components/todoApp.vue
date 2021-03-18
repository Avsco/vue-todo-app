<template>
  <section class="todo">
    <h1 class="todo__title">TODO</h1>
    <todo-form />
    <todo-list v-if="todos.length !== 0" />
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

    return { todos };
  }
};
</script>

<style scoped lang="scss">
.todo {
  margin-top: 5rem;
  width: 76vw;

  @media (min-width: 1015px) {
    width: 60vw;
  }
}

.todo__title {
  color: white;
  font-weight: 700;
  font-size: 3rem;
}
</style>
