<template>
  <div class="salesWrap">
    {{ gender }}
  </div>
</template>

<script>
export default {
  name: "sales",
  props: ["gender"],
  data: function () {
    return {
      collection: [
        { name: "T-shirt", regularPrice: 39.99, newPrice: 29.99 },
        { name: "shirt", regularPrice: 89.99, newPrice: 59.99 },
        { name: "jacket", regularPrice: 69.99, newPrice: 49.99 },
        { name: "T-shirt", regularPrice: 119.99, newPrice: 100 },
        { name: "shirt", regularPrice: 40, newPrice: 30.99 },
        { name: "shirt", regularPrice: 75, newPrice: 65 },
        { name: "jacket", regularPrice: 129.99, newPrice: 99.99 },
        { name: "T-shirt", regularPrice: 29.99, newPrice: 19 },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";

.salesWrap {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: auto;
  gap: 1.5em;
}
</style>