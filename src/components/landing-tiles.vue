<template>
  <div class="tiles-container">
    <div class="tile" id="sales">
      <h2>sales</h2>
      <h3>do - 50%</h3>
    </div>
    <div class="tile" id="newForHer">
      <h2>nowości</h2>
      <h3>dla niej</h3>
    </div>
    <div class="tile" id="newForHim">
      <h2>nowości</h2>
      <h3>dla niego</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "landing-tiles",
  data: function() {
    return {
      tiles: {
        proposed: [
          {
            name: "item_1",
            img: "https://via.placeholder.com/200x300",
            price: "59.99zł",
          },
          {
            name: "item_2",
            img: "https://via.placeholder.com/200x300",
            price: "29.99zł",
          },
          {
            name: "item_3",
            img: "https://via.placeholder.com/200x300",
            price: "89.99zł",
          },
          {
            name: "item_4",
            img: "https://via.placeholder.com/200x300",
            price: "119.99zł",
          },
          {
            name: "item_5",
            img: "https://via.placeholder.com/200x300",
            price: "79.99zł",
          },
          {
            name: "item_6",
            img: "https://via.placeholder.com/200x300",
            price: "129.99zł",
          },
        ],
      },
    };
  },
};
</script>

<style lang="scss">
@import "../styles/common.scss";

.tiles-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 2em;
  padding: 2em 0;

  .tile {
    width: 350px;
    padding: 8em 0;
    background-image: url("https://via.placeholder.com/300x400");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    text-transform: uppercase;

    h2 {
      font-weight: bold;
    }
  }
}
</style>
