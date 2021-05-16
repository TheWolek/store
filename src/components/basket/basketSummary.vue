<template>
  <div class="summary">
    <div class="price">
      <p>Łączna kwota</p>
      <p>{{ sum }}</p>
    </div>
    <hr />
    <form>
      <button class="discountBtn">
        Mam kod rabatowy
        <div class="discountBtnIcon">
          <span></span>
          <span></span>
        </div>
      </button>
      <input type="submit" value="Przejdź do dostawy" class="btn-primary" />
    </form>
  </div>
</template>

<script>
export default {
  name: "basket-summary",
  props: ["sum"],
};
</script>

<style lang="scss">
</style>