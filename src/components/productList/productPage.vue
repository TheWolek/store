<template>
  <div>
    <div v-if="loading">LOADING...</div>
    <div v-if="err != undefined">{{ err.msg }}</div>
    <div class="productPage" v-if="!loading && err == undefined">
      <div class="productImgHolder">
        <div id="productImgPrev"></div>
        <img src="https://via.placeholder.com/400x600" />
        <div id="productImgNext"></div>
      </div>
      <div class="productDetails">
        <h3>{{ item.name }}</h3>
        <p class="newPrice">{{ item.newPrice }} zł</p>
        <p class="regPrice">{{ item.regularPrice }} zł</p>
        <form v-on:submit="this.formValidation">
          <div class="form-group">
            <select name="size" id="size" v-model="selectedSize">
              <option selected hidden>Wybierz rozmiar</option>
              <option value="xs">XS</option>
              <option value="s">S</option>
              <option value="m">M</option>
              <option value="l">L</option>
              <option value="xl">XL</option>
            </select>
            <div v-if="err != undefined" id="err">{{ err }}</div>
            <input type="submit" value="Dodaj do koszyka" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "productPage",
  props: ["inputItemId"],
  data: function () {
    return {
      item: {},
      selectedSize: undefined,
      err: undefined,
      loading: true,
    };
  },
  methods: {
    formValidation(e) {
      e.preventDefault();
      if (this.selectedSize == undefined) {
        this.err = "wybierz rozmiar";
        return;
      }
      this.err = undefined;
      this.$router.push({ name: "Basket", params: { itemToPush: this.item } });
    },
  },
  mounted: function () {
    const item = fetch("http://localhost:5000/collection/" + this.inputItemId)
      .then((res) => res.json())
      .then((data) => {
        if (data.status == 404) {
          this.loading = false;
          this.err = { status: data.status, msg: data.err };
          return;
        }
        this.loading = false;
        this.err = undefined;
        this.item = data[0];
      });
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";

.productPage {
  display: flex;
  justify-content: space-around;
  flex-direction: column;

  .productImgHolder {
    overflow: hidden;
  }

  .productDetails {
    display: flex;
    flex-wrap: wrap;

    h3 {
      padding: 0.8em 0 0.3em 0.3em;
      width: 100%;
      text-align: left;
      margin: 0;
    }

    p {
      font-size: 1.5rem;
      padding: 0 0 0 0.3em;
    }

    .regPrice {
      text-decoration: line-through;
    }

    .newPrice {
      color: $font-red;
      font-weight: bold;
      margin-right: 1em;
    }

    form {
      width: 100%;

      select {
        width: 95%;
        padding: 0.5em;
      }

      #err {
        color: $font-red;
        font-weight: bold;
      }

      input {
        margin-top: 1.5em;
        width: 95%;
        border: 0;
        background: $bg-black;
        color: white;
        padding: 0.8em;
        font-weight: bold;
      }
    }
  }
}
</style>