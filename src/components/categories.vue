<template>
  <ol class="categories">
    <li>
      <a id="salesCategory">Sales</a>
    </li>
    <li id="womanCategory" class="dropdown">
      <a
        class="dropdown-toggle"
        data-toggle="dropdown"
        href="#"
        role="button"
        aria-haspopup="true"
        aria-expanded="false"
      >
        Ona
      </a>
      <ul id="womanCategoryList" class="dropdown-menu">
        <li
          v-for="(cat, name) in womanCategories"
          :key="name"
          class="dropdown-menu-item"
        >
          {{ name }}
          <ul>
            <li v-for="item in cat" :key="item" class="category-item">
              {{ item }}
            </li>
          </ul>
        </li>
      </ul>
    </li>
    <li id="manCategory" class="dropdown">
      <a
        class="dropdown-toggle"
        data-toggle="dropdown"
        href="#"
        role="button"
        aria-haspopup="true"
        aria-expanded="false"
      >
        On
      </a>
      <ul id="manCategoryList" class="dropdown-menu">
        <li
          v-for="(cat, name) in manCategories"
          :key="name"
          class="dropdown-menu-item"
        >
          {{ name }}
          <ul>
            <li v-for="item in cat" :key="item" class="category-item">
              {{ item }}
            </li>
          </ul>
        </li>
      </ul>
    </li>
    <li>
      <a id="newCategory">Nowości</a>
    </li>
  </ol>
</template>

<script>
export default {
  name: "categories",
  data: function() {
    return {
      //in future this will be fetched from API...
      womanCategories: {
        kolekcja: [
          "Sukienki",
          "Koszule",
          "T-shirty",
          "Bluzy",
          "Swetry",
          "Spodnie",
          "Spódnice",
          "Szorty",
        ],
        dodatki: [
          "Buty",
          "Torby, plecaki",
          "Skarpetki, bielizna",
          "Czapki",
          "Portfele",
          "Biżuteria",
          "Okulary",
          "Stroje kąpielowe",
        ],
      },
      manCategories: {
        kolekcja: [
          "T-shirty",
          "Szorty",
          "Koszule",
          "Bluzy",
          "Spodnie",
          "Kurtki, płaszcze",
        ],
        dodatki: [
          "Buty",
          "Okulary",
          "Czapki",
          "Skarpetki",
          "Torby, plecaki",
          "Paski",
          "Portfele",
        ],
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../styles/common.scss";

ol {
  list-style-type: none;
  display: flex;
  width: 100%;
  justify-content: flex-start;
  gap: 1em;
}

ol,
ul {
  list-style: none;
}

ol > li {
  width: 4vw;
  border-top-left-radius: 4%;
  border-top-right-radius: 4%;

  &:hover {
    cursor: pointer;
  }

  a {
    display: block;
    width: 100%;
    height: 100%;
  }
}

.dropdown {
  ul {
    cursor: default;
  }
}

.dropdown-menu {
  width: 20em;
  left: -5em !important;
  gap: 1.7em;
  text-transform: uppercase;
  padding-left: 0.7em;
}

#manCategoryList {
  left: -10.8em !important;
}

.dropdown-menu.show {
  display: flex;
}

.dropdown-menu-item {
  ul {
    font-weight: normal;
    text-transform: capitalize;
    padding-left: 1em;
    padding-top: 0.5em;

    li + li {
      padding-top: 0.6em;
    }
  }
}

.category-item:hover {
  cursor: pointer;
}

#salesCategory {
  text-transform: uppercase;
  color: $font-red;
  font-size: 1.1rem;
}
</style>
