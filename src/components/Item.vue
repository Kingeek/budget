<template>
  <div class="item">
    <div class="image">
      <img src="" alt="">
    </div>
    <span class="name">Item title</span>
  </div>  
</template>

<script>
export default {
  name: "Item"
};
</script>

<style lang="scss">
.item {
  .image {
    width: 40px;
    height: 40px;
    display: inline-block;
    vertical-align: middle;
    border-radius: 5px;
    background-color: #d1d1d1;
    margin-right: 25px;
  }

  .name {
    font-size: 18px;
    font-weight: 600;
  }
}
</style>
