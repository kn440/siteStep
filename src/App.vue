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
const ProductsPage = () => import('./components/ProductsPage.vue');

//import ProductsPage from './components/ProductsPage.vue';
const ContactMapPage = () => import('./components/ContactMapPage.vue');
//import ContactMapPage from './components/ContactMapPage.vue';
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
  metaInfo() {
    return {
      title: 'Незамерзайка в Одинцово - Купить автохимию',
      meta: [
        {
          name: 'description',
          content: 'Купить незамерзайку в Одинцово. Доставка по Одинцово и МО.'
        },
        {
          name: 'keywords',
          content: 'незамерзайка, Одинцово, автохимия, доставка, Доставка по Одинцово и МО, зимняя жидкость, антифриз, жидкость для стеклоомывателя, зимняя автохимия, автохимия Одинцово, покупка незамерзайки, незамерзающая жидкость, вода незамерзающая, жижа, зимняя антифриз жидкость, автохимия для зимы, зимняя жидкость для автомобиля, незамерзайка для стеклоомывателя, зимний автохимический состав, автохимия для холодной погоды, зимняя жидкость для охлаждения, качественная незамерзайка,недорогая автохимия в Одинцово, antifreeze, car antifreeze, winter antifreeze, antifreeze fluid, auto antifreeze, car windshield fluid, winter windshield fluid, antifreeze for cars, coolant antifreeze, automotive antifreeze, antifreeze for winter, best antifreeze, antifreeze liquid, antifreeze 50/50, antifreeze store, antifreeze in Odenzovo,buy antifreeze online, antifreeze for windshield wipers, antifreeze for engine cooling'
        }
      ]
    };
  }
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
