<template>
  <li class="item">
    <span :class="`item__text${todo.status ? '--done' : ''}`">
      {{ todo.todo }}
    </span>
    <span @click="handlerStatus(todo.id)">V</span>
    <span @click="hadlerDeleteTodo(todo.id)">X</span>
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
    function handlerStatus(id) {
      emit("todo-complete", id);
    }

    function hadlerDeleteTodo(id) {
      emit("todo-delete", id);
    }

    return { handlerStatus, hadlerDeleteTodo };
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
