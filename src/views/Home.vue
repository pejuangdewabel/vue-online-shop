<template>
  <div class="home">
    <header-home />
    <hero-home />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderHome from "../components/HeaderHome.vue";

import HeroHome from "../components/HeroHome.vue";

export default {
  name: "Home",
  components: {
    HeaderHome,
    HeroHome,
  },
};
</script>
