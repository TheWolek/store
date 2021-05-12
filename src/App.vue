<template>
  <div
    id="app"
    class="container col-12 col-sm-12 col-md-12 col-lg-10 col-xl-10"
  >
    <Navi />
    <router-view />
    <Foter />
  </div>
</template>

<script>
import Navi from "./components/nav";
import Foter from "./components/foter";

export default {
  name: "app",
  components: {
    Navi,
    Foter,
  },
};
</script>

<style lang="scss">
@import "/styles/common.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $font-dark;
}
</style>
