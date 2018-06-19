<template>
  <main class="right-side">
    <Header />
    <Content />
  </main>
</template>

<script>
import Header from "./Header.vue";
import Content from "./Content.vue";

export default {
  name: "Main",
  props: {},
  components: {
    Header,
    Content
  }
};
</script>

<style lang="scss">
.right-side {
  flex-grow: 1;
  text-align: center;
}
</style>
