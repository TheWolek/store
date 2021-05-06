<template>
  <div id="nav">
    <div class="menu">
      <router-link to="/">
        <img alt="Vue logo" src="../assets/logo.png" />
      </router-link>
      <router-link to="/account">Twoje konto</router-link>
      <router-link to="/basket">Koszyk</router-link>
    </div>
    <categories />
  </div>
</template>

<script>
import Categories from "./categories.vue";

export default {
  name: "navi",
  components: {
    Categories,
  },
};
</script>

<style lang="scss">
@import "../styles/common.scss";

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: $font-dark;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
