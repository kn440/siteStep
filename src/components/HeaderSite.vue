<template>
  <header class="header">
    <div class="header-content">
      <!-- Логотип всегда грузим -->
      <div class="logo">
        <img src="@/assets/img/logo.svg" alt="Незамерзайка" />
        <div class="site-info" v-if="!isMobile">
          <span class="site-title">Продажа незамерзающей жидкости</span>
          <span class="site-subtitle">Сертифицированный продукт высокого качества</span>
          <span class="site-subtitle">город Одинцово</span>
        </div>
      </div>
      
      <!-- Контактная информация: менеджер, телефон, соцсети -->
      <div class="contact-info" v-if="!isMobile">
        <img
          class="manager-photo"
          :src="managerPhoto"
          alt="Фото менеджера"
          loading="lazy"
        />
        <div class="phone-contact">
          <a href="tel:+79057007039" class="phone-number">+7 (905) 700-70-39</a>
        </div>
        <div class="social-links">
          <a href="https://t.me/Chugundyrka" target="_blank" class="telegram-icon" v-html="telegramSvg"></a>
        </div>
      </div>

      <!-- Навигация -->
      <nav class="navigation" v-if="!isMobile">
        <ul>
          <li><a href="#products" class="products-link">Продукция</a></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderSite',
  data() {
    return {
      isMobile: false,
      managerPhoto: require('@/assets/img/photo_manager.webp'),

      telegramSvg: `
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="12" cy="12" r="12" fill="#0088cc"/>
          <path d="M17.55 6.45C17.85 6.3 18.15 6.6 18.05 6.95L15.75 15.45C15.65 15.8 15.3 15.9 15.05 15.75L12.55 14.05L11.45 15.05C11.35 15.15 11.2 15.25 11 15.2L11.1 12.65L15.6 8.9C15.8 8.75 15.6 8.5 15.35 8.65L9.1 12.15L6.7 11.35C6.35 11.25 6.35 10.8 6.75 10.7L17.55 6.45Z" fill="white"/>
        </svg>
      `
    };
  },
  mounted() {
    this.isMobile = window.innerWidth <= 768;
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #004b8d, #0072b8);
  padding: 15px 20px;
  color: #ffffff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.header-content {
  display: flex;
  justify-content: space-between;
  width: 100%;
  max-width: 1200px;
  align-items: center;
}

.logo {
  display: flex;
  align-items: center;
}

.logo img {
  height: 50px;
  margin-right: 10px;
}

.site-info {
  display: flex;
  flex-direction: column;
}

.site-title {
  font-size: 1.5rem;
  font-weight: 600;
}

.site-subtitle {
  font-size: 0.9rem;
  font-weight: 400;
  color: #d0d0d0;
}

.contact-info {
  display: flex;
  align-items: center;
  margin-right: 20px;
}

.manager-photo {
  height: 40px;
  width: 40px;
  border-radius: 50%;
  margin-right: 15px;
}

.phone-contact {
  margin-right: 15px;
}

.phone-number {
  color: #ffffff;
  text-decoration: none;
  font-size: 1rem;
  font-weight: 500;
}

.phone-number:hover {
  color: #ffdd00;
}

.social-links {
  display: flex;
  gap:10px;
}

.navigation ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.navigation li {
  margin: 0 20px;
}

.products-link {
  color: #f7f6f6;
  font-size: 1.6rem;
  font-weight: 600;
  text-decoration: none;
  position: relative;
}

.products-link::before {
  content: '';
  position: absolute;
  left: -20px;
  top: 50%;
  transform: translateY(-50%);
  width: 4px;
  height: 40px;
  background-color: red;
}

.products-link:hover {
  color: #c2cdd5;
}
</style>
