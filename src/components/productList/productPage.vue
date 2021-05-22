<template>
  <div>{{ id }}</div>
</template>

<script>
export default {
  name: "productPage",
  props: ["id"],
  data: function () {
    return {
      item: { id: this.id, name: "test", price: "test" },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";
</style>