<template>
  <div class="landing">
    <div id="carousel">
      <div id="imgHolder"></div>
      <div id="dots">
        <div id="pic1" class="active"></div>
        <div id="pic2"></div>
        <div id="pic3"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "landing",
};
</script>

<style scoped lang="scss">
@import "../styles/common.scss";

.landing {
  #carousel {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: relative;

    #imgHolder {
      width: 100%;
      height: 400px;
      background-image: url("https://via.placeholder.com/330x400");
      background-repeat: no-repeat;
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

        &:hover {
          cursor: pointer;
        }
      }

      .active {
        background: $bg-black;
      }
    }
  }
}

@media screen and (min-width: 768px) {
  .landing {
    #carousel {
      #imgHolder {
        width: 100%;
        height: 400px;
        background-image: url("https://via.placeholder.com/738x400");
        background-repeat: no-repeat;
      }
    }
  }
}

@media screen and (min-width: 1024px) {
  .landing {
    #carousel {
      #imgHolder {
        width: 100%;
        height: 400px;
        background-image: url("https://via.placeholder.com/1570x400");
        background-repeat: no-repeat;
      }

      #dots {
        div {
          width: 16px;
          height: 16px;
        }
      }
    }
  }
}
</style>
