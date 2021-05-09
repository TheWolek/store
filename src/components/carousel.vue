<template>
  <div id="carousel">
    <div id="imgHolder">
      <div id="imgFrame">
        <div id="prevImg" />
        <div id="activeImg" />
        <div id="nextImg" />
      </div>
    </div>
    <div id="dots">
      <div id="0" v-on:click="SelectSlide" class="active"></div>
      <div id="1" v-on:click="SelectSlide"></div>
      <div id="2" v-on:click="SelectSlide"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "carousel",
  data: function() {
    return {
      activeSlide: 0,
    };
  },
  methods: {
    selectDot: function(dotId) {
      document.querySelectorAll("#dots div").forEach((item) => {
        item.classList.remove("active");
      });

      $("#" + dotId).addClass("active");
    },

    SelectSlide: function(event) {
      let selectedSlide = event.target.id;
      this.changeSlide(parseInt(selectedSlide));
    },

    changeSlide: function(slideId) {
      console.log("change slide to: ", slideId);
      this.selectDot(slideId);
      switch (slideId) {
        case 0:
          $("#imgFrame").css("transform", "translateX(1620px)");
          break;

        case 1:
          $("#imgFrame").css("transform", "translateX(0)");
          break;

        case 2:
          $("#imgFrame").css("transform", "translateX(-1620px)");
          break;
      }

      this.activeSlide = slideId;
    },
  },
  //   mounted: function() {
  //     window.setInterval(() => {
  //       if (this.activeSlide == 2) {
  //         this.changeSlide(0);
  //         return;
  //       }

  //       this.changeSlide(this.activeSlide + 1);
  //     }, 5000);
  //   },
};
</script>

<style lang="scss">
@import "../styles/common.scss";

#carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;

  #imgHolder {
    width: 100%;
    height: 400px;
    overflow-x: hidden;
    display: flex;
    justify-content: center;

    #imgFrame {
      display: flex;
      justify-content: center;
      gap: 20px;
      transition: all 1s ease-in-out;
      transform: translateX(1620px);

      div {
        width: 1600px;
        height: 400px;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
      }

      #prevImg {
        background-image: url("https://via.placeholder.com/1600x410");
      }

      #activeImg {
        background-image: url("https://via.placeholder.com/1600x400");
      }

      #nextImg {
        background-image: url("https://via.placeholder.com/1600x420");
      }
    }
  }

  #dots {
    width: 250px;
    height: 50px;
    position: absolute;
    bottom: 1em;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5em;

    div {
      width: 20px;
      height: 20px;
      background: $bg-black-trans;
      border-radius: 50%;
      transition: all 0.3s ease;

      &:hover {
        cursor: pointer;
      }
    }

    .active {
      background: $bg-black;
    }
  }
}

@media screen and (min-width: 768px) {
  #carousel {
    #imgHolder {
      width: 100%;
      height: 400px;
      // background-image: url("https://via.placeholder.com/738x400");
      // background-repeat: no-repeat;
    }
  }
}

@media screen and (min-width: 1024px) {
  #carousel {
    #imgHolder {
      width: 100%;
      height: 400px;
      // background-image: url("https://via.placeholder.com/1570x400");
      // background-repeat: no-repeat;
    }

    #dots {
      div {
        width: 16px;
        height: 16px;
      }
    }
  }
}
</style>
