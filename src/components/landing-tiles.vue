<template>
  <div class="tiles">
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
    <div class="tiles-carousel">
      <div id="tilesPrev">
        <img src="../assets/prev.png" />
      </div>
      <div id="tilesFrame">
        <div class="tile" v-for="tile in tiles" :key="tile.name">
          <div class="imgFrame"></div>
          <p class="itemName">{{ tile.name }}</p>
          <p class="itemPrice">{{ tile.price }}</p>
        </div>
      </div>
      <div id="tilesNext">
        <img src="../assets/next.png" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "landing-tiles",
  data: function() {
    return {
      tiles: [
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
        {
          name: "item_7",
          img: "https://via.placeholder.com/200x300",
          price: "109.99zł",
        },
        {
          name: "item_8",
          img: "https://via.placeholder.com/200x300",
          price: "59.99zł",
        },
        {
          name: "item_9",
          img: "https://via.placeholder.com/200x300",
          price: "79.99zł",
        },
        {
          name: "item_10",
          img: "https://via.placeholder.com/200x300",
          price: "19.99zł",
        },
        {
          name: "item_11",
          img: "https://via.placeholder.com/200x300",
          price: "29.99zł",
        },
        {
          name: "item_12",
          img: "https://via.placeholder.com/200x300",
          price: "39.99zł",
        },
      ],
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

.tiles-carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-x: hidden;
  position: relative;

  #tilesFrame {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    transition: all 0.8s ease-in-out;
    transform: translateX(730px); //-730

    .tile {
      padding: 3em 0;
      width: 240px;
      background: yellow;
    }
  }

  #tilesPrev,
  #tilesNext {
    position: absolute;
    z-index: 10;
    font-weight: bold;
    font-size: 2rem;
    top: 50%;
    transform: translateY(-50%);

    img {
      height: 32px;
    }

    &:hover {
      cursor: pointer;
    }
  }

  #tilesPrev {
    left: 1em;
  }

  #tilesNext {
    right: 1em;
  }
}
</style>
