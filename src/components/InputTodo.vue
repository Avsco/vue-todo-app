<template>
  <input v-model="todo" type="text" placeholder="Create a new todo..." />
  <span @click="clearInput">X</span>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    let todo = ref("");

    function clearInput() {
      todo.value = "";
    }

    return { todo, clearInput };
  }
};
</script>

<style scoped lang="scss"></style>
