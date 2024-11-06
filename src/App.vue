<template>
  <div id="app">
    <HeaderSite />
    <HeroImage  />
    <ProductsPage id="products" />
    <SpacerComponent />
    <ContactMapPage />
    <SpacerComponent />
    <FooterSite />
  </div>
</template>
<script>

import FooterSite from './components/FooterSite.vue';
import HeaderSite from './components/HeaderSite.vue';

import HeroImage from './components/HeroImage.vue';
import ProductsPage from './components/ProductsPage.vue';
import ContactMapPage from './components/ContactMapPage.vue';
import SpacerComponent from './components/SpacerComponent.vue';

export default {
  components: {
    HeaderSite,
    FooterSite,
    ContactMapPage,
    HeroImage,
    ProductsPage,
    SpacerComponent,
    
  },
};
</script>
<style lang="scss">
#app {
  font-family: Avenir,'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html {
  scroll-behavior: smooth;
}
body {
  font-family: 'Roboto', sans-serif; /* Замените 'Roboto' на название вашего шрифта */
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
