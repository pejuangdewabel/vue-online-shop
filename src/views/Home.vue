<template>
  <div class="home">
    <header-home />
    <hero-home />
    <product-owl />
    <instagram />
    <partner />
    <footer-home />
  </div>
</template>

<script>
import FooterHome from "../components/FooterHome.vue";
// @ is an alias to /src
import HeaderHome from "../components/HeaderHome.vue";
import HeroHome from "../components/HeroHome.vue";
import Instagram from "../components/Instagram.vue";
import Partner from "../components/Partner.vue";
import ProductOwl from "../components/ProductOwl.vue";

export default {
  name: "Home",
  components: {
    HeaderHome,
    HeroHome,
    ProductOwl,
    Instagram,
    Partner,
    FooterHome,
  },
};
</script>
