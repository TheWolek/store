<template>
  <div class="itemsWrap">{{ gender }}</div>
</template>

<script>
export default {
  name: "productlist",
  props: ["gender"],
  data: function () {},
  mounted: function () {
    console.log("test");
    $(".itemsWrap").css("opacity", "1");
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";
</style>