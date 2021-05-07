<template>
  <div
    id="app"
    class="container col-12 col-sm-12 col-md-12 col-lg-10 col-xl-10"
  >
    <Navi />
    <router-view />
    <div>
      Icons made by
      <a href="https://www.freepik.com" title="Freepik">Freepik</a> and
      <a href="https://www.flaticon.com/authors/iconixar" title="iconixar"
        >iconixar</a
      >
      from
      <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>
    </div>
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
