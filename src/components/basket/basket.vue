<template>
  <div class="basket-wrap">
    <div class="basket-empty" v-if="this.basket[0] == undefined">
      <h3>Twój koszyk jest pusty</h3>
      <router-link to="/">Powrót na stronę głowną</router-link>
    </div>
    <div class="basket" v-else>
      <div>
        <div class="bar">
          <h4>Koszyk ({{ countBasket() }})</h4>
          <div class="clearBasket" v-on:click="clearBasket">Wyczyść koszyk</div>
        </div>
        <ul>
          <li v-for="item in this.basket" :key="item.id">
            <div class="item-imgHolder"></div>
            <p class="item-name">{{ item.name }}</p>
            <p class="item-price">{{ item.price + " zł" }}</p>
            <div
              class="delete"
              v-on:click="
                () => {
                  deleteItem(item.id);
                }
              "
            >
              <img class="DeleteBlack" src="../../assets/delete.png" />
              <img class="DeleteRed" src="../../assets/deleteRed.png" />
            </div>
          </li>
        </ul>
      </div>
      <basketSummary v-bind:sum="BasketSum" @activeCode="updateBasket" />
    </div>
  </div>
</template>

<script>
import basketSummary from "./basketSummary";

export default {
  name: "Basket",
  components: {
    basketSummary,
  },
  props: ["itemToPush"],
  methods: {
    sumBasket: function () {
      let total = 0;
      this.basket.map((item) => {
        total += item.price;
      });

      this.BasketSum = total;
      return;
    },

    updateBasket: function (e) {
      let newSum = this.BasketSum - this.BasketSum * (e / 100);
      newSum = Math.round(newSum * 100) / 100;
      this.BasketSum = newSum;
    },

    addToBasket: function (newItem) {
      newItem.price = newItem.newPrice;
      this.basket.push(newItem);
      this.setCookie("basket", { basket: this.basket });
    },

    setCookie: function (key, newValue) {
      this.$cookies.set(key, newValue);
      console.log("set cookies", this.$cookies.get(key));
    },

    countBasket: function () {
      return this.basket.length;
    },

    clearBasket: function () {
      this.basket = [];
      this.setCookie("basket", { basket: this.basket });
    },

    deleteItem: function (e) {
      console.log(e);
    },
  },
  data: function () {
    return {
      // basket: [
      //   { id: 20, name: "buty", price: 49.99 },
      //   { id: 10, name: "T-shirt", price: 29.99 },
      // ],
      basket: [],
      BasketSum: 0,
    };
  },
  mounted: function () {
    window.setTimeout(() => {
      if (this.$cookies.get("basket") == null) {
        this.setCookie("basket", { basket: this.basket });
      } else {
        console.log("get cookies", this.$cookies.get("basket"));
        this.basket = this.$cookies.get("basket").basket;
      }
      if (this.itemToPush != undefined) this.addToBasket(this.itemToPush);
      this.sumBasket();
    }, 10);
  },
};
</script>

<style lang="scss">
@import "../../styles/common.scss";

.basket-wrap {
  padding: 1em 0;
  .basket {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 2em;

    .bar {
      display: flex;
      padding: 0.5em 1em;

      h4 {
        text-align: left;
        width: 70%;
      }

      div {
        &:hover {
          cursor: pointer;
        }
      }
    }

    ul {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 1.5em;
      padding: 0 0.5em;

      li {
        display: grid;
        padding: 0.8em 1em;
        border: 1px solid $font-dark;
        height: 90px;
        grid-template-columns: [left] 15vw [center] 1fr [centerRight] 1fr 10vw;
        grid-template-rows: auto;
        place-items: center;
        gap: 0.6em;

        p {
          margin: 0;
        }

        .item-name {
          grid-column: center;
          justify-self: flex-start;
        }

        .item-price {
          grid-column: centerRight;
          font-weight: bold;
        }

        .item-imgHolder {
          background-image: url("https://via.placeholder.com/300x300");
          background-position: center;
          background-size: cover;
          background-repeat: no-repeat;
          height: 100%;
          width: 100%;
          grid-column: left;
        }

        .delete {
          position: relative;
          .DeleteRed {
            height: 24px;
            position: absolute;
            top: 0;
            left: 0;
            transition: all 0.2s ease;
            will-change: opacity;
            opacity: 0;
          }

          img {
            height: 24px;
          }

          .DeleteRed:hover {
            cursor: pointer;
            opacity: 1;
          }
        }
      }
    }
  }
}

@media screen and (min-width: 1024px) {
  .basket-wrap {
    .basket {
      flex-direction: row;
      justify-content: space-around;
    }
  }
}
</style>