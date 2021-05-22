<template>
  <div>
    <div class="salesSelect">
      <button
        class="active"
        id="leftBtn"
        @click="
          () => {
            changeGender(0);
          }
        "
      >
        <div class="btnBg left"></div>
        <span>dla niej</span>
      </button>
      <button
        id="rightBtn"
        @click="
          () => {
            changeGender(1);
          }
        "
      >
        <div class="btnBg right"></div>
        <span>dla niego</span>
      </button>
    </div>
    <Sales v-bind:gender="this.selectedGender" />
  </div>
</template>

<script>
import Sales from "../components/productList/sales";

export default {
  name: "sales",
  components: { Sales },
  data: function () {
    return {
      selectedGender: 0,
    };
  },
  methods: {
    changeGender: function (selected) {
      if (selected == 0) {
        this.selectedGender = 0;
        $("#leftBtn").addClass("active");
        $("#rightBtn").removeClass("active");
        return;
      }

      this.selectedGender = 1;
      $("#leftBtn").removeClass("active");
      $("#rightBtn").addClass("active");
    },
  },
};
</script>

<style lang="scss">
@import "../styles/common.scss";

.salesSelect {
  display: flex;
  justify-content: center;
  gap: 1em;
  button {
    border: 0;
    background: none;
    padding: 0.5em;
    text-transform: uppercase;
    transition: background 0.3s ease;
    overflow: hidden;
    position: relative;
    border-radius: 3%;

    span {
      display: block;
      position: relative;
      z-index: 2;
    }

    .btnBg {
      position: absolute;
      top: 0;
      left: 0;
      background: $bg-yellow;
      width: 100%;
      height: 100%;
      transition: all 0.3s ease-in-out;
      z-index: 1;
    }

    .btnBg.left {
      transform: translateX(-110%);
    }

    .btnBg.right {
      transform: translateX(110%);
    }
  }

  #leftBtn:hover .left {
    transform: translateX(0);
  }

  #rightBtn:hover .right {
    transform: translateX(0);
  }

  button.active span {
    font-weight: bold;
  }
}
</style>