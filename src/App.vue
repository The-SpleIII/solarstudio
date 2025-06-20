<template>
  <div class="min-h-screen overflow-hidden relative">
    <IconField />
    <Header />
    <Hero @open-products="showProducts = true" />
    <Products @select="openModal" />
    <Services />
    <Reviews />
    <Footer />
    <ModalProduct
      v-if="modalProduct"
      :product="modalProduct"
      @close="modalProduct = null"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import Products from "./components/Products.vue";
import Services from "./components/Services.vue";
import Reviews from "./components/Reviews.vue";
import Footer from "./components/Footer.vue";
import ModalProduct from "./components/ModalProduct.vue";
const showProducts = ref(false);
const modalProduct = ref(null);

function openModal(prod) {
  modalProduct.value = prod;
}
</script>
