<template>
  <div class="landing">
    <carousel />
    <landing-tiles />
  </div>
</template>

<script>
import carousel from "./carousel.vue";
import LandingTiles from "./landing-tiles.vue";
export default {
  components: { carousel, LandingTiles },
  name: "landing",
};
</script>
