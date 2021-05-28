<template>
  <productPage v-bind:inputItem="$route.params.item" />
</template>

<script>
import productPage from "../components/productList/productPage";
export default {
  name: "productPageView",
  components: { productPage },
  mounted: function () {
    console.log(this.$route);
  },
};
</script>