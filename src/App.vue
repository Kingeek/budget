<template>
  <div id="app">
    <!-- <Aside /> -->
    <Main />
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Aside from "./components/Aside.vue";

export default {
  name: "app",
  components: {
    Main,
    Aside
  }
};
</script>

<style lang="scss">
@import "../src/assets/css/reset.css";
@import "../src/assets/css/fonts.scss";

#app {
  display: flex;
  justify-content: space-between;
  align-content: stretch;
  align-items: stretch;
  min-height: 100vh;
}
</style>
