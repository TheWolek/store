<template>
  <Basket v-bind:itemToPush="$route.params.itemToPush" />
</template>

<script>
import Basket from "../components/basket/basket.vue";
export default {
  name: "basket",
  components: { Basket },
};
</script>