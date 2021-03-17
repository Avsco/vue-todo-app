<template>
  <li class="item">
    <span :class="`item__text${todo.status ? '--done' : ''}`">
      {{ todo.todo }}
    </span>
    <span @click="markAsComplete(todo.id)">V</span>
    <span @click="deleteTodo(todo.id)">X</span>
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

<style scoped lang="scss">
.item {
  &__text {
    &--done {
      text-decoration-line: line-through;
    }
  }
}
</style>
