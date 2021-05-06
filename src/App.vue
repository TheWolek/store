<template>
  <div id="app">
    <Navi />
    <router-view />
  </div>
</template>

<script>
import Navi from "./components/nav";

export default {
  name: "app",
  components: {
    Navi,
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
