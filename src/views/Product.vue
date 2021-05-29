<template>
  <div class="product">
    <header-home />
    <p>
      Halaman Product
    </p>
    <footer-home />
  </div>
</template>
<script>
import FooterHome from "../components/FooterHome.vue";
import HeaderHome from "../components/HeaderHome.vue";
export default {
  name: "Product",
  components: {
    HeaderHome,
    FooterHome,
  },
};
</script>
