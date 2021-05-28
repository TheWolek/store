<template>
  <div class="productPage">
    <div class="productImgHolder">
      <img src="https://via.placeholder.com/450x650" />
    </div>
    <div class="productDetails">
      <h1>{{ item.name }}</h1>
      <p class="newPrice">{{ item.newPrice }}</p>
      <p class="regPrice">{{ item.regularPrice }}</p>
    </div>
  </div>
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

.productPage {
  display: flex;
  justify-content: space-around;

  .productImgHolder {
    overflow: hidden;
  }

  .productDetails {
    display: flex;
    flex-wrap: wrap;

    h1 {
      width: 100%;
    }

    .regPrice {
      text-decoration: line-through;
    }

    .newPrice {
      color: $font-red;
      font-weight: bold;
      font-size: 1.2rem;
    }
  }
}
</style>