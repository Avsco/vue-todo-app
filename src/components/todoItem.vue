<template>
  <li>{{ todo }}</li>
</template>

<script>
export default {
  name: "todoItem",

  props: {
    todo: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped lang="scss"></style>
