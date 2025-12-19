<template>
  <div class="main_class" v-if="showHero">
    <section class="hero-image">
      <div class="hero-image-container">
        <img 
          :src="heroSrc" 
          alt="Изображение незамерзайки" 
          class="hero-image" 
          loading="lazy"
        />
      </div>
      <div class="hero-content">
        <h1 class="slogan">Мы продаем только то, что сами используем</h1>
        <p class="description">
          Предлагаемая продукция сертифицирована и заслужила высокую оценку среди наших покупателей.
        </p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "HeroImage",
  data() {
    return {
      showHero: false,
      heroSrc: require('@/assets/img/photo_main.webp') // WebP для быстрого отображения
    };
  },
  mounted() {
    // Проверяем ширину экрана
    if (window.innerWidth > 480) {
      this.showHero = true;
    }
  }
};
</script>

  
  <style scoped>
.main_class{
    
    display: flex;
    justify-content: center;
    align-items: center;
   
}

  .hero-image {
    display: flex;
    flex-direction: row; /* Переставляет картинку перед текстом */
    align-items: center;
    justify-content: center;
    padding: 60px 0px 15px 0px; 
    width: 90%;
    max-width: 1200px;
    height: auto;
    border-radius: 12px;
    object-fit: cover;
    
    
  }
  
  .hero-image-container {
    
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 20px; /* Отступ между изображением и текстом */
  }
  
  
  
  .hero-content {
    flex: 1;
    text-align: left;
    margin-top: -40px;
    padding: 0 20px;
  }
  
  .slogan {
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 15px;
    position: relative; /* Необходимо для позиционирования псевдоэлемента */
  }
  .slogan::before {
    content: '';
    position: absolute;
    left: -20px; /* Расстояние от текста */
    top: 50%;
    transform: translateY(-50%); /* Центрирование по вертикали */
    width: 4px; /* Ширина линии */
    height: 100px; /* Высота линии */
    background-color: red; /* Цвет линии */
  }
  
  .description {
    font-size: 1.25rem;
    line-height: 1.6;
    
  }
/* Адаптация для мобильных устройств */
@media (max-width: 480px) {
  .main_class{
    display: none;
  }
}
  
  </style>
  