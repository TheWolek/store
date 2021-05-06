<template>
  <ul class="categories">
    <li>
      <a id="salesCategory">Sales</a>
    </li>
    <li>
      <a id="womanCategory">Ona</a>
      <ul>
        <li v-for="cat in womanCategories" :key="cat">{{ cat }}</li>
      </ul>
    </li>
    <li>
      <a id="manCategory">On</a>
      <ul>
        <li v-for="cat in manCategories" :key="cat">{{ cat }}</li>
      </ul>
    </li>
    <li>
      <a id="newCategory">Nowości</a>
    </li>
  </ul>
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
.categories {
  list-style-type: none;
  display: flex;

  ul {
    list-style: none;
  }
}
</style>
