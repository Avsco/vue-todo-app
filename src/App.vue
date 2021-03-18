<template>
  <main class="app">
    <div class="app__image"></div>
    <todo-app />
  </main>
</template>

<script>
import todoApp from "./components/todoApp.vue";

export default {
  components: {
    todoApp
  }
};
</script>

<style lang="scss">
*,
*::after,
*::before {
  box-sizing: border-box;
}

:root {
  --background: #ffab91;
  --primary-color: #fff;
  --secondary-color: #bf360c;
  --font-color: #000;
  --border-radius: 5px;
}

:is(h1, h2, h3, h4, h5, h6, p) {
  margin: 0;
}

body {
  margin: 0;
  padding: 0;

  background: var(--background);
  color: var(--font-color);
}

.app {
  display: flex;
  justify-content: center;
  margin: 0;
  height: 0;
  min-height: 100vh;

  &__image {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    height: 40vh;
    width: 100%;
    background-image: url("./assets/orange-texture.jpg");
  }
}
</style>
