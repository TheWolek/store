<template>
  <div class="summary">
    <div class="price">
      <p>Łączna kwota</p>
      <p>{{ sum }}zł</p>
    </div>
    <div class="discounts" v-if="usedDiscounts.lenght != 0">
      <p v-for="code in usedDiscounts" :key="code">
        - {{ countDiscount(code) }} zł
      </p>
    </div>
    <hr />
    <form>
      <button id="discountBtn">
        <span v-on:click="changeDiscoundForm">Mam kod rabatowy</span>
        <div id="discountBtnIcon" v-on:click="changeDiscoundForm">
          <span></span>
          <span></span>
        </div>
        <form id="promoCodeForm" v-on:submit="this.checkCode">
          <p id="errMsg"></p>
          <input
            type="text"
            id="promoCode"
            name="promoCode"
            v-model="promoCode"
          />
          <input type="submit" value="Aktywuj" />
        </form>
      </button>
      <input
        type="submit"
        value="Przejdź do dostawy"
        class="btn-primary NextBtn"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "basket-summary",
  props: ["sum"],
  data: function () {
    return {
      discoundFormActive: false,
      discountCodes: {
        TEN: 10,
        MISIA: 50,
      },
      usedDiscounts: [],
      promoCode: null,
    };
  },
  methods: {
    changeDiscoundForm: function () {
      if (!this.discoundFormActive) {
        $("#discountBtnIcon").addClass("discountFormActive");
        $("#discountBtn").css("paddingBottom", "6.5em");
        $("#errMsg").html("");
        this.discoundFormActive = true;
        return;
      }

      $("#discountBtnIcon").removeClass("discountFormActive");
      $("#discountBtn").css("padding", "0.2em");
      $("#errMsg").html("");
      this.discoundFormActive = false;
      return;
    },

    checkCode: function (e) {
      e.preventDefault();
      if (this.usedDiscounts.includes(this.promoCode)) {
        $("#errMsg").html("Kod został już użyty");
        this.promoCode = null;
        return false;
      }

      if (!this.findCode()) {
        this.promoCode = null;
        $("#errMsg").html("Błędny kod");
      }
    },

    findCode: function () {
      if (
        Object.prototype.hasOwnProperty.call(this.discountCodes, this.promoCode)
      ) {
        this.changeDiscoundForm();
        this.usedDiscounts.push(this.discountCodes[this.promoCode]);
        this.$emit("activeCode", this.discountCodes[this.promoCode]);
        this.promoCode = null;
        $("#errMsg").html("");
        return true;
      }

      return false;
    },

    countDiscount: function (disc) {
      let output = this.sum * (disc / 100);
      output = Math.round(output * 100) / 100;
      return output;
    },
  },
};
</script>

<style lang="scss">
@import "../../styles/common.scss";

hr {
  background: $font-dark;
}

.summary {
  .price {
    display: flex;
    justify-content: space-around;
    font-weight: bold;

    p {
      margin: 0;
    }
  }

  .discounts {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    padding-right: 3.5em;
    gap: 0.5em;

    p {
      margin: 0;
    }
  }

  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 1.5em;

    #discountBtn {
      border: 1px solid $font-dark;
      border-radius: 10px;
      width: 70%;
      height: 32px;
      position: relative;
      padding: 0.2em;
      overflow: hidden;
      transition: all 0.5s ease;

      span {
        display: block;
        width: 100%;
        height: 30px;
      }

      #discountBtnIcon {
        position: absolute;
        top: 15px;
        transform: translateY(-50%);
        right: 0.5em;
        width: 25px;
        height: 25px;
        transition: all 0.3s ease;

        span {
          width: 15px;
          height: 3px;
          background: $font-dark;
          position: absolute;
          top: 0;
          right: 0;
        }

        span:nth-child(1) {
          transform: rotate(45deg) translate(7px, 7px);
        }

        span:nth-child(2) {
          // background: green;
          transform: rotate(-45deg) translate(-13px, 0px);
        }
      }

      form {
        margin-top: 0.5em;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        gap: 0;
        justify-content: center;

        #errMsg {
          width: 100%;
          margin: 0;
          color: $font-red;
          font-weight: bold;
        }

        input[type="text"] {
          width: 60%;
          border: 1px solid $font-dark;
          border-right: none;
          padding: 0.2em;
        }

        input[type="submit"] {
          width: 30%;
          border: 1px solid $font-dark;
          border-radius: 0;
          border-top-right-radius: 10px;
          border-bottom-right-radius: 10px;
          padding: 0.2em 0.5em;
          background: $bg-green;
          font-weight: bold;
        }
      }

      .discountFormActive {
        transform: rotate(-180deg) translateY(13px) !important;
      }
    }

    .NextBtn {
      border-radius: 10px;
      width: 75%;
      padding: 0.2em;
    }
  }
}

@media screen and (min-width: 768px) {
  form {
    #discountBtn {
      width: 50%;
    }

    .NextBtn {
      width: 55%;
      padding: 0.35em;
    }
  }
}

@media screen and (min-width: 1024px) {
  .summary {
    width: 30%;
    min-height: 300px;
    box-shadow: 0px 5px 15px -4px rgba(0, 0, 0, 0.4),
      0px 0px 20px -4px rgba(0, 0, 0, 0.4);
    padding: 1em;
    border: 1px solid rgba(0, 0, 0, 0.4);

    form {
      #discountBtn {
        width: 70%;
      }

      .NextBtn {
        width: 75%;
      }
    }
  }
}
</style>