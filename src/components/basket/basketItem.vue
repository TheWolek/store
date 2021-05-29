<template>
  <li>
    <div class="item-imgHolder"></div>
    <p class="item-name">{{ item.name }}</p>
    <p class="item-price">{{ item.price + " zł" }}</p>
    <div class="delete" v-on:click="EmitDelete">
      <img class="DeleteBlack" src="../../assets/delete.png" />
      <img class="DeleteRed" src="../../assets/deleteRed.png" />
    </div>
  </li>
</template>

<script>
export default {
  name: "basketItem",
  props: ["inputItem"],
  data: function () {
    return {
      item: {},
    };
  },
  methods: {
    EmitDelete: function () {
      this.$emit("delete", this.item.BasketID);
    },
  },
  mounted: function () {
    this.item = this.inputItem;
  },
};
</script>