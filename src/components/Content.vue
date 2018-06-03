<template>
  <section class="content">
    <Item />
  </section>  
</template>

<script>
import Item from "./Item.vue";

export default {
  name: "Content",
  components: {
    Item
  }
};
</script>

<style lang="scss">
.content {
  padding: 50px 40px;
}
</style>
