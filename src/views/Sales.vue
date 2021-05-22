<template>
  <div>
    <div class="salesSelect">
      <div
        class="btn active"
        id="leftBtn"
        @click="
          (e) => {
            e.preventDefault();
            changeGender(0);
          }
        "
      >
        <div class="btnBg left"></div>
        <span>dla niej</span>
      </div>
      <div
        class="btn"
        id="rightBtn"
        @click="
          (e) => {
            e.preventDefault();
            changeGender(1);
          }
        "
      >
        <div class="btnBg right"></div>
        <span>dla niego</span>
      </div>
    </div>
    <SalesMain v-bind:gender="this.selectedGender" :key="genderKey" />
  </div>
</template>

<script>
import SalesMain from "../components/productList/salesMain";

export default {
  name: "sales",
  components: { SalesMain },
  data: function () {
    return {
      selectedGender: 0,
      genderKey: 0,
    };
  },
  methods: {
    changeGender: function (selected) {
      this.genderKey += 1;
      if (selected == 0) {
        $("#rightBtn").removeClass("active");
        $("#leftBtn").addClass("active");
        this.selectedGender = 0;
      } else {
        $("#rightBtn").addClass("active");
        $("#leftBtn").removeClass("active");
        this.selectedGender = 1;
      }
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
  .btn {
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

  .btn.active span {
    font-weight: bold;
  }
}
</style>