<template>
  <section class="content">
    <SlickList lockAxis="y" :useDragHandle=true v-model="items" class="list-unstyled">
      <SlickItem v-for="(item, index) in items" :index="index" :key="index">
        <Item :data="item" />
      </SlickItem>
    </SlickList>
    <div class="item input">
      <div class="image"></div>
      <div class="flex">
        <input class="name" placeholder="name" v-model="Name" @keydown.enter="nextFocus">
        <input class="value" placeholder="value" v-model="Value" @keydown.enter="addItem">
      </div>
    </div>
    <div class="footer">
      <span class="total">TOTAL: {{total}}</span>
    </div>
  </section>  
</template>

<script>
import { SlickList, SlickItem, HandleDirective } from "vue-slicksort";
import Item from "./Item.vue";

export default {
  name: "Content",
  components: {
    Item,
    SlickItem,
    SlickList
  },
  data: function() {
    return {
      Name: "",
      Value: "",
      total: null,
      items: []
    };
  },
  methods: {
    addItem() {
      this.items.push({ name: this.Name, value: this.Value });
      this.Name = "";
      this.Value = "";
    }
  },
  mounted() {
    if (localStorage.getItem("items")) {
      this.items = JSON.parse(localStorage.getItem("items"));
      for (var i = 0; i <= this.items.length; i++) {
        this.total += parseInt(this.items[i].value);
      }
    }
  },
  watch: {
    items: {
      handler() {
        localStorage.setItem("items", JSON.stringify(this.items));
      },
      deep: true
    }
  }
};
</script>

<style scoped lang="scss">
.content {
  padding: 50px 40px;
  text-align: center;
  max-width: 620px;
  margin: 0 auto;
}

.list-unstyled {
  list-style: none;
}

.item {
  padding: 10px;
  border-radius: 5px;
  transition: 0.15s ease;
  max-width: 600px;

  &.input {
    margin-bottom: 20px;
  }

  &:hover {
    background-color: #fafafa;
  }

  .image {
    width: 40px;
    height: 40px;
    display: inline-block;
    vertical-align: middle;
    border-radius: 5px;
    background-color: #e7e7e7;
    margin-right: 15px;
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
    border: none;
    padding: 5px 10px;
    outline: none;
  }

  .value {
    font-size: 18px;
    font-weight: 600;
    display: inline-block;
    vertical-align: middle;
    border: none;
    padding: 5px 10px;
    outline: none;
    text-align: right;
    width: 100px;

    &::after {
      content: "$";
      display: inline-block;
      margin-left: 5px;
    }
  }
}

.footer {
  position: sticky;
  background-color: #fff;
  bottom: 0;
  padding: 20px;
  text-align: right;
  border-top: 1px solid #e8e8e8;

  .total {
    font-size: 20px;
    font-weight: 600;
    color: #262e42;

    &::after {
      content: "€";
      display: inline-block;
      margin-left: 5px;
    }
  }
}
</style>
