<template>
  <li>
    {{ todo.todo }}
    <span @click="deleteTodo(todo.id)">V</span>
    <span @click="markAsComplete(todo.id)">X</span>
  </li>
</template>

<script>
export default {
  name: "todoItem",
  emits: ["todo-complete", "todo-delete"],
  props: {
    todo: {
      type: Object,
      require: true
    }
  },

  setup(_, { emit }) {
    function markAsComplete(id) {
      emit("todo-complete", id);
    }

    function deleteTodo(id) {
      emit("todo-delete", id);
    }

    return { markAsComplete, deleteTodo };
  }
};
</script>

<style scoped lang="scss"></style>
