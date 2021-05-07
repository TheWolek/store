<template>
  <div class="home">
    <landing msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import landing from "@/components/landing.vue";

export default {
  name: "Home",
  components: {
    landing,
  },
};
</script>
