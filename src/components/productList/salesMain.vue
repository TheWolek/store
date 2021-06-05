<template>
  <div>
    <div v-if="loading" id="loading">LOADING...</div>
    <div v-if="!loading" class="itemsWrap">
      <router-link
        v-for="item in collection"
        :key="item.id"
        v-bind:to="{ path: `product/${item.id}`, params: { item_id: item.id } }"
        class="tile"
      >
        <div class="imgHolder">
          <img src="https://via.placeholder.com/350x500" />
        </div>
        <div class="itemDetails">
          <p class="name">{{ item.name }}</p>
          <p class="newPrice">{{ item.newPrice }}zł</p>
          <p class="regularPrice">{{ item.regularPrice }}zł</p>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "salesMain",
  props: ["gender"],
  data: function () {
    return {
      //depedning of what gender is selected, diffrent collection would be fetch from DB
      // collection: [
      //   { id: 0, name: "T-shirt", regularPrice: 39.99, newPrice: 29.99 },
      //   { id: 1, name: "shirt", regularPrice: 89.99, newPrice: 59.99 },
      //   { id: 2, name: "jacket", regularPrice: 69.99, newPrice: 49.99 },
      //   { id: 3, name: "T-shirt", regularPrice: 119.99, newPrice: 100 },
      //   { id: 4, name: "shirt", regularPrice: 40, newPrice: 30.99 },
      //   { id: 5, name: "shirt", regularPrice: 75, newPrice: 65 },
      //   { id: 6, name: "jacket", regularPrice: 129.99, newPrice: 99.99 },
      //   { id: 7, name: "T-shirt", regularPrice: 29.99, newPrice: 19 },
      // ],
      collection: [],
      loading: true,
    };
  },
  mounted: function () {
    this.fetchData(this.gender);
    window.setTimeout(() => {
      this.loading = false;
    }, 500);
    window.setTimeout(() => {
      $(".itemsWrap").css("opacity", "1");
    }, 500);
  },
  methods: {
    fetchData: function (gender) {
      if (gender == 0) gender = "female";
      else gender = "male";
      const data = fetch("http://localhost:5000/sales/" + gender)
        .then((res) => res.json())
        .then((data) => (this.collection = data));
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/common.scss";

#loading {
  width: 100%;
  height: 30vh;
  font-size: 1.5rem;
  display: grid;
  place-items: center;
  font-weight: bold;
}

.itemsWrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  // grid-template-columns: repeat(4, 1fr);
  // grid-template-rows: auto;
  gap: 1.5em;
  opacity: 0;
  transition: all 1s ease;
  padding: 1em 0;

  .tile {
    &:hover {
      cursor: pointer;
      text-decoration: none;
    }

    &:hover img {
      transform: scale(1.1);
    }

    .imgHolder {
      overflow: hidden;
    }

    img {
      transition: all 0.3s ease-in-out;
    }
    .itemDetails {
      color: $font-dark;
      text-decoration: none;
      p {
        margin: 0;
      }

      .name {
        margin: 0.3em 0;
      }

      .newPrice {
        color: $font-red;
        font-weight: bold;
        font-size: 1.1em;
      }

      .regularPrice {
        text-decoration: line-through;
      }
    }
  }
}
</style>