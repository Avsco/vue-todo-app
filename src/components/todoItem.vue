<template>
  <li>{{ todo.todo }}</li>
</template>

<script>
export default {
  name: "todoItem",

  props: {
    todo: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped lang="scss"></style>
