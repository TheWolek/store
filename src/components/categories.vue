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
        <li v-for="cat in womanCategories" :key="cat" class="dropdown-item">
          {{ cat }}
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
        <li v-for="cat in manCategories" :key="cat" class="dropdown-item">
          {{ cat }}
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
      womanCategories: ["sukienki", "koszule", "T-shirty"],
      manCategories: ["T-shirty", "szorty", "bluzy"],
    };
  },
};
</script>

<style lang="scss" scoped>
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
  // border: 1px solid #000;
  border-top-left-radius: 4%;
  border-top-right-radius: 4%;

  &:hover {
    // box-shadow: rgba(0, 0, 0, 8%) 0px 0px 2px 1px;
    cursor: pointer;
  }

  a {
    display: block;
    width: 100%;
  }
}

.dropdown-menu {
  width: 20em;
  margin-left: -95px;
}
</style>
