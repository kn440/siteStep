<template>
    <div class="contact-map-container">

    <div class="contact-map-page">
      <div class="manager-info">
        <img :src="manager.photo" alt="Менеджер" class="manager-photo" />
        <h2>{{ manager.name }}</h2>
        <span>{{ manager.description }}</span>
  
        <div class="contact-details">
          <p><strong>Телефон:</strong> <a :href="`tel:${manager.phone}`">{{ manager.phone }}</a></p>
            <p><strong>Почта:</strong> <a :href="`mailto:${manager.email}`">{{ manager.email }}</a></p>
            <a href="https://t.me/Chugundyrka" target="_blank" style="text-decoration: none;">
                <button style="padding: 10px 20px; background-color: #0088cc; color: white; border: none; border-radius: 5px; cursor: pointer;">
                    Написать в Telegram
                </button>
            </a>
            <p></p>
            <a href="https://wa.me/+79057007039" target="_blank" style="text-decoration: none;">
                <button style="padding: 10px 20px; background-color: #25D366; color: white; border: none; border-radius: 5px; cursor: pointer;">
                    Написать в WhatsApp
                </button>
            </a>
          </div>
  
       <!--  <button @click="requestCallback" class="callback-button">Заказать обратный звонок</button> -->
      </div>
  
      <div class="map-container">
        <span style="text-align: left;">Адрес для самовывоза: город Одинцово, улица Комсомольская, дом 18</span>
        <p></p>
        <div class="map-base">
            <div id="map" style="width: 100%; height: 400px;"></div></div>
      </div>
    </div></div>
  </template>
  
  <script>
  export default {
    name: 'ContactMapPage',
    data() {
      return {
        manager: {
          name: 'Степанов Степан',
          photo: require('@/assets/img/photo_manager.jpg'),
          description: 'Профессиональный менеджер с более чем 12-летним опытом в сфере продаж.',
          phone: '+7 (905) 700-70-39',
        email: 'steeepan@mail.ru',
        },
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
            zoom: 18
          });
  
          // Добавление маркера (достопримечательности)
          const placemark = new ymaps.Placemark([55.665771, 37.293038], {
            balloonContent: 'Самовывоз. Адрес: г. Одинцово, ул. Комсомольская, д.18'
          });
  
          this.map.geoObjects.add(placemark);
        });
      },
  
      requestCallback() {
        alert('Обратный звонок будет заказан!');
      },
    },
  };
  </script>
  
  <style scoped>
  .contact-map-container {
    padding: 0 20px; /* Задаем отступы слева и справа */
    max-width: 1200px; /* Максимальная ширина страницы */
    margin: 0 auto; /* Центрируем контейнер */
  }
  .contact-map-page {
    display: flex;
    flex-direction: row;
    gap: 20px;
    padding: 20px;
  }
  
  .manager-info {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .manager-photo {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    margin-bottom: 10px;
  }
  
  .manager-stats {
    list-style: none;
    padding: 0;
    margin: 10px 0;
  }
  
  .manager-stats li {
    font-size: 14px;
    margin: 5px 0;
  }
  
  .callback-button {
    padding: 10px 15px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .callback-button:hover {
    background-color: #0056b3;
  }
  
  .map-container {
    flex: 2;
  }
  
  @media (max-width: 768px) {
    .contact-map-page {
      flex-direction: column;
    }
  
    .map-container {
      width: 100%;
      margin-top: 20px;
    }
  }
  </style>
  