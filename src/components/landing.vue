<template>
  <div class="landing">
    <carousel />
  </div>
</template>

<script>
import carousel from "./carousel.vue";
export default {
  components: { carousel },
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
