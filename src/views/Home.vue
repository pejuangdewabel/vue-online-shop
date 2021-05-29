<template>
  <div class="home">
    <header-home />
    <hero-home />
    <product-owl />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderHome from "../components/HeaderHome.vue";
import HeroHome from "../components/HeroHome.vue";
import ProductOwl from "../components/ProductOwl.vue";

export default {
  name: "Home",
  components: {
    HeaderHome,
    HeroHome,
    ProductOwl,
  },
};
</script>
