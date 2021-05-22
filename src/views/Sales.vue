<template>
  <div>
    <div class="salesSelect">
      <button class="active" id="leftBtn">
        <div class="btnBg left"></div>
        <span>dla niej</span>
      </button>
      <button id="rightBtn">
        <div class="btnBg right"></div>
        <span>dla niego</span>
      </button>
    </div>
    <Sales />
  </div>
</template>

<script>
import Sales from "../components/productList/sales";

export default {
  name: "sales",
  components: { Sales },
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
      transform: translateX(-100%);
    }

    .btnBg.right {
      transform: translateX(100%);
    }
  }

  #leftBtn:hover .left {
    transform: translateX(0);
  }

  #rightBtn:hover .right {
    transform: translateX(0);
  }

  button.active {
    font-weight: bold;
  }
}
</style>