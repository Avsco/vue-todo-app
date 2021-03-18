<template>
  <li class="item">
    <span>
      <span
        type="checkbox"
        :class="`item__done ${todo.status ? 'item__done--selected' : ''}`"
        @click="handlerStatus(todo.id)"
      />
      <p :class="`item__text ${todo.status ? 'item__text--done' : ''}`">
        {{ todo.todo }}
      </p>
    </span>
    <span class="item__delete" @click="hadlerDeleteTodo(todo.id)" />
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
  display: flex;
  justify-content: space-between;
  padding-left: 1rem;

  &__text {
    display: inline;
    font-size: 1.2rem;
    word-break: break-word;

    &--done {
      text-decoration-line: line-through;
    }
  }

  &__done {
    display: inline-block;
    height: 17px;
    width: 17px;
    border: 1px solid lightgray;
    border-radius: 50%;
    margin-right: 15px;
    transition: background-color 300ms ease-in-out;

    &:hover,
    &--selected {
      background-color: var(--secondary-color);
    }
  }

  &__delete {
    &:after {
      content: "\274c";
      color: #fff;
    }
  }
}
</style>
