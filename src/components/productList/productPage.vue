<template>
  <div>{{ item }}</div>
</template>

<script>
export default {
  name: "productPage",
  props: ["inputItem"],
  data: function () {
    return {
      item: this.inputItem,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";
</style>