<template>
  <div class="tiles">
    <div class="tiles-container">
      <div class="tile" id="sales">
        <div class="cover"></div>
        <h2>sales</h2>
        <h3>do - 50%</h3>
      </div>
      <div class="tile" id="newForHer">
        <div class="cover"></div>
        <h2>nowości</h2>
        <h3>dla niej</h3>
      </div>
      <div class="tile" id="newForHim">
        <div class="cover"></div>
        <h2>nowości</h2>
        <h3>dla niego</h3>
      </div>
    </div>
    <div class="tiles-carousel">
      <div
        id="tilesPrev"
        v-on:click="
          () => {
            moveCarousel(0);
          }
        "
      >
        <img src="../assets/prev.png" />
      </div>
      <div id="tilesFrame">
        <div class="tile" v-for="tile in tiles" :key="tile.name">
          <div class="imgFrame"></div>
          <p class="itemName">{{ tile.name }}</p>
          <p class="itemPrice">{{ tile.price }}</p>
        </div>
      </div>
      <div
        id="tilesNext"
        v-on:click="
          () => {
            moveCarousel(1);
          }
        "
      >
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
      carouselStage: 720,
      start: 720,
      end: -780,
      tiles: [
        {
          name: "item_1",
          img: "https://via.placeholder.com/200x300",
          price: "59.99 PLN",
        },
        {
          name: "item_2",
          img: "https://via.placeholder.com/200x300",
          price: "29.99 PLN",
        },
        {
          name: "item_3",
          img: "https://via.placeholder.com/200x300",
          price: "89.99 PLN",
        },
        {
          name: "item_4",
          img: "https://via.placeholder.com/200x300",
          price: "119.99 PLN",
        },
        {
          name: "item_5",
          img: "https://via.placeholder.com/200x300",
          price: "79.99 PLN",
        },
        {
          name: "item_6",
          img: "https://via.placeholder.com/200x300",
          price: "129.99 PLN",
        },
        {
          name: "item_7",
          img: "https://via.placeholder.com/200x300",
          price: "109.99 PLN",
        },
        {
          name: "item_8",
          img: "https://via.placeholder.com/200x300",
          price: "59.99 PLN",
        },
        {
          name: "item_9",
          img: "https://via.placeholder.com/200x300",
          price: "79.99 PLN",
        },
        {
          name: "item_10",
          img: "https://via.placeholder.com/200x300",
          price: "19.99 PLN",
        },
        {
          name: "item_11",
          img: "https://via.placeholder.com/200x300",
          price: "29.99 PLN",
        },
        {
          name: "item_12",
          img: "https://via.placeholder.com/200x300",
          price: "39.99 PLN",
        },
      ],
    };
  },
  methods: {
    controlArrows() {
      if (this.carouselStage <= this.end) {
        $("#tilesNext").css("display", "none");
      } else {
        $("#tilesNext").css("display", "block");
      }

      if (this.carouselStage >= this.start) {
        $("#tilesPrev").css("display", "none");
      } else {
        $("#tilesPrev").css("display", "block");
      }
    },

    moveCarousel: function(dir) {
      if (dir > 0) {
        let step = this.carouselStage - 250;
        $("#tilesFrame").css("transform", `translateX(${step}px)`);
        this.carouselStage = step;

        this.controlArrows();
      } else {
        let step = this.carouselStage + 250;
        $("#tilesFrame").css("transform", `translateX(${step}px)`);
        this.carouselStage = step;

        this.controlArrows();
      }
    },
  },

  mounted: function() {
    this.carouselStage = 1320;
    this.start = 1320;
    this.end = -1430;

    if (window.screen.width >= 768) {
      this.carouselStage = 1130;
      this.start = 1130;
      this.end = -1120;
    }

    if (window.screen.width >= 1024) {
      this.carouselStage = 720;
      this.start = 720;
      this.end = -780;
    }
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
    overflow: hidden;
    position: relative;

    .cover {
      width: 100%;
      height: 100%;
      background: rgb(255, 232, 25);
      position: absolute;
      top: 0;
      transform: translateY(100%);
      transition: all 0.5s cubic-bezier(0.22, 0.61, 0.36, 1);
      z-index: 1;
    }

    &:hover .cover {
      transform: translateY(0);
    }

    &:hover h2,
    &:hover h3 {
      transform: scale(1.15);
    }

    h2,
    h3 {
      position: relative;
      z-index: 2;
      will-change: scale;
      transition: all 0.5s ease;
    }

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
  margin-top: 2em;

  #tilesFrame {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    transition: all 0.4s ease-in-out;
    transform: translateX(1320px); //

    .tile {
      // padding-top: 16em;
      width: 240px;

      .imgFrame {
        padding-top: 16em;
        background: url("https://via.placeholder.com/300x400");
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
      }

      .itemName {
        font-weight: bold;
        margin-bottom: 0.2em;
      }
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
    transition: filter 0.3s ease;

    img {
      height: 32px;
    }

    &:hover {
      cursor: pointer;
      filter: contrast(0.4);
    }
  }

  #tilesPrev {
    left: 1em;
    display: none;
  }

  #tilesNext {
    right: 1em;
  }
}

@media screen and(min-width: 768px) {
  .tiles-carousel {
    #tilesFrame {
      transform: translateX(1130px); //-720
    }
  }
}

@media screen and(min-width: 1024px) {
  .tiles-carousel {
    #tilesFrame {
      transform: translateX(720px); //-720
    }
  }
}
</style>
