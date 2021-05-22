<template>
  <productPage v-bind:id="$route.params.id" />
</template>

<script>
import productPage from "../components/productList/productPage";
export default {
  name: "productPageView",
  components: { productPage },
};
</script>