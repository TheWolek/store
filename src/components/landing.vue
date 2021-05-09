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

<style scoped lang="scss">
@import "../styles/common.scss";

.landing {
}

@media screen and (min-width: 768px) {
  .landing {
  }
}

@media screen and (min-width: 1024px) {
  .landing {
  }
}
</style>
