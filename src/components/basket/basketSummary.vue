<template>
  <div class="summary">
    <div class="price">
      <p>Łączna kwota</p>
      <p>{{ sum }} zł</p>
    </div>
    <hr />
    <form>
      <button id="discountBtn" v-on:click="changeDiscoundForm">
        Mam kod rabatowy
        <div id="discountBtnIcon">
          <span></span>
          <span></span>
        </div>
        <form>
          <input type="text" id="promoCode" name="promoCode" />
          <input type="submit" value="Aktywuj" />
        </form>
      </button>
      <input type="submit" value="Przejdź do dostawy" class="btn-primary" />
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
    };
  },
  methods: {
    changeDiscoundForm: function () {
      if (!this.discoundFormActive) {
        $("#discountBtnIcon").addClass("discountFormActive");
        $("#discountBtn").css("paddingBottom", "5em");
        this.discoundFormActive = true;
        return;
      }

      $("#discountBtnIcon").removeClass("discountFormActive");
      $("#discountBtn").css("padding", "0.2em");
      this.discoundFormActive = false;
      return;
    },
  },
};
</script>

<style lang="scss">
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1.5em;

  #discountBtn {
    border: 1px solid #000;
    border-radius: 10px;
    width: 70%;
    height: 32px;
    position: relative;
    padding: 0.2em;
    overflow: hidden;
    transition: all 0.5s ease;

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
        background: #000;
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
      gap: 0;
      justify-content: center;

      input[type="text"] {
        width: 60%;
        border: 1px solid #000;
        border-right: none;
        padding: 0.2em;
      }

      input[type="submit"] {
        width: 30%;
        border: 1px solid #000;
        border-radius: 0;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        padding: 0.2em 0.5em;
        background: rgb(56, 233, 56);
        font-weight: bold;
      }
    }

    .discountFormActive {
      transform: rotate(-180deg) translateY(13px) !important;
    }
  }

  input[type="submit"] {
    border-radius: 10px;
    width: 75%;
    padding: 0.2em;
  }
}
</style>