<template>
  <div class="product">
    <header-home />
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="breadcrumb-text product-more">
              <a href="./home.html"><i class="fa fa-home"></i> Home</a>
              <span>Detail</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="row">
              <div class="col-lg-6">
                <div class="product-pic-zoom">
                  <img class="product-big-img" :src="gambar_default" alt="" />
                </div>
                <div
                  class="product-thumbs"
                  v-if="productDetails.galleries.length > 0"
                >
                  <carousel
                    class="product-thumbs-track ps-slider"
                    :dots="false"
                    :nav="false"
                    :autoplay="true"
                  >
                    <div
                      v-for="ss in productDetails.galleries"
                      :key="ss.id"
                      class="pt"
                      @click="changeImage(ss.photo)"
                      :class="ss.photo == gambar_default ? 'active' : ''"
                    >
                      <img :src="ss.photo" alt="" />
                    </div>
                  </carousel>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="product-details text-left">
                  <div class="pd-title">
                    <span>{{ productDetails.type }}</span>
                    <h3>{{ productDetails.name }}</h3>
                  </div>
                  <div class="pd-desc">
                    <p v-html="productDetails.description"></p>
                    <h4>{{ productDetails.price }}</h4>
                  </div>
                  <div class="quantity">
                    <a href="shopping-cart.html" class="primary-btn pd-cart"
                      >Add To Cart</a
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Product Shop Section End -->

    <related-product />
    <footer-home />
  </div>
</template>
<script>
import carousel from "vue-owl-carousel";
import FooterHome from "../components/FooterHome.vue";
import HeaderHome from "../components/HeaderHome.vue";
import RelatedProduct from "../components/RelatedProduct.vue";

import axios from "axios";

export default {
  name: "Product",
  components: {
    HeaderHome,
    FooterHome,
    carousel,
    RelatedProduct,
  },
  data() {
    return {
      gambar_default: "",
      thumbs: [
        "img/mickey1.jpg",
        "img/mickey2.jpg",
        "img/mickey3.jpg",
        "img/mickey4.jpg",
      ],
      // idProduct: this.$route.params.id,
      productDetails: [],
    };
  },
  methods: {
    changeImage(urlImage) {
      this.gambar_default = urlImage;
      // console.log(this.idProduct);
    },
    setDataPicture(data) {
      this.productDetails = data;
      this.gambar_default = data.galleries[0].photo;
    },
  },
  mounted() {
    axios
      .get("http://backend-onlineshop.test:8080/api/products", {
        params: {
          id: this.$route.params.id,
        },
      })
      .then((res) => this.setDataPicture(res.data.data))
      .catch((err) => console.log(err));
  },
};
</script>
<style scoped>
.product-thumbs .pt {
  margin-right: 16px;
}
</style>
