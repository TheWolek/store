<template>
  <div class="navi col-12">
    <div class="menu">
      <router-link to="/">
        <img alt="Vue logo" src="../assets/logo.png" />
      </router-link>
      <div class="links">
        <router-link to="/account">
          <img src="../assets/account.png" alt="account" />
          <div>Twoje konto</div>
        </router-link>
        <router-link to="/basket">
          <img src="../assets/basket.png" alt="basket" />
          <div>Koszyk</div>
        </router-link>
      </div>
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

.navi {
  // padding: 20px 30px;

  a {
    font-weight: bold;
    color: $font-dark;

    &.router-link-exact-active {
      color: #42b983;
    }
  }

  .menu {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    padding: 1em;

    img {
      height: 70px;
    }

    a:nth-child(1) {
      justify-self: flex-start !important;
    }

    .links {
      width: 10vw;
      height: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;

      a {
        color: $font-dark;
        transition: all 0.1s ease;
        border-radius: 8%;
        padding: 0.3em;

        &:hover {
          color: lighten($color: $font-dark, $amount: 15%);
        }

        &:hover img {
          filter: contrast(0.3);
        }

        img {
          height: 35px;
          transition: all 0.1s ease;
        }
      }
    }
  }
}
</style>
