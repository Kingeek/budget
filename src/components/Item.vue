<template>
  <div class="item">
    <div class="image">
      <img :src="'//logo.clearbit.com/'+data.name+'.com'">
    </div>
    <div class="flex">
      <span class="name">{{data.name}}</span>
      <span class="value">{{data.value}}</span>
    </div>
  </div>  
</template>

<script>
export default {
  name: "Item",
  props: {
    data: {
      type: Object
    }
  }
};
</script>

<style scoped lang="scss">
.item {
  padding: 10px;
  border-radius: 5px;
  transition: 0.15s ease;
  max-width: 600px;

  &:hover {
    background-color: #fafafa;
  }

  .image {
    width: 40px;
    height: 40px;
    display: inline-block;
    vertical-align: middle;
    border-radius: 5px;
    background-color: #d1d1d1;
    margin-right: 15px;

    img {
      object-fit: contain;
      width: 100%;
      height: 100%;
    }
  }

  .flex {
    display: inline-flex;
    vertical-align: middle;
    justify-content: space-between;
    align-content: center;
    align-items: center;
    width: calc(100% - 70px);
  }

  .name {
    font-size: 18px;
    font-weight: 600;
    display: inline-block;
    vertical-align: middle;
    padding: 5px 10px;
  }

  .value {
    font-size: 18px;
    font-weight: 600;
    display: inline-block;
    vertical-align: middle;
    text-align: right;
    padding: 5px 10px;
  }
}
</style>
