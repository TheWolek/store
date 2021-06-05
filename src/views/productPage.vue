<template>
  <productPage v-bind:inputItemId="$route.params.id" />
</template>

<script>
import productPage from "../components/productList/productPage";
export default {
  name: "productPageView",
  components: { productPage },
};
</script>