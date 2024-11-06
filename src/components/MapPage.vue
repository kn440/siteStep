<template> <div class="map-base">
    <div id="map" style="width: 100%; height: 400px;"></div></div>
  </template>
  
  <script>
  export default {
    name: 'MapPage',
    data() {
      return {
        map: null,
      };
    },
    mounted() {
      // Динамически загружаем скрипт Яндекс.Карты
      if (!window.ymaps) {
        const script = document.createElement('script');
        script.src = 'https://api-maps.yandex.ru/2.1/?lang=ru_RU&apikey=c2b0dfc1-31f6-4657-9e61-01bbe8a37555';
        script.onload = this.initMap;
        document.head.appendChild(script);
      } else {
        this.initMap();
      }
    },
    methods: {
      initMap() {
        window.ymaps.ready(() => {
          this.map = new ymaps.Map("map", {
            center: [55.665771, 37.293038], // 
            zoom: 15
          });
  
          // Добавление маркера (достопримечательности)
          const placemark = new ymaps.Placemark([55.665771, 37.29], {
            balloonContent: ''
          });
  
          this.map.geoObjects.add(placemark);
        });
      }
    }
  };
  </script>
  
  <style scoped>

  .map-base{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 40px;
  }

  #map {
   
    height: 400px;
    display: flex;
    background-color: #f7f7f7;
    border-radius: 10px;
    padding: 20px;
    max-width: 1200px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  </style>
  