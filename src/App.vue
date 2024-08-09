<template>
  <div id="app">
    <NavBar />
    <CarouselPag />
    <ProductsPag />
    <FooterPag />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import CarouselPag from './components/CarouselPag.vue';
import ProductsPag from './components/ProductsPag.vue';
import FooterPag from './components/FooterPag.vue';


export default {
  name: 'App',
  components: {
    NavBar,
    CarouselPag,
    ProductsPag,
    FooterPag
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
</style>
