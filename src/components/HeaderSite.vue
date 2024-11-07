<template>
    <header class="header">
      <div class="header-content">
        <div class="logo">
          <img src="@/assets/img/logo.svg" alt="Незамерзайка" />
          <div class="site-info">
            <span class="site-title">Продажа незамерзающей жидкости </span>
            <span class="site-subtitle">Сертифицированный продукт высокого качества</span>
            <span class="site-subtitle">город Одинцово</span>
          </div>
        </div>
        
        <div class="contact-info">
          <img class="manager-photo" src="@/assets/img/photo_manager.jpg" alt="Фото менеджера" />
          <div class="phone-contact">
            <a href="tel:+79057007039" class="phone-number">+7 (905) 700-70-39</a>
          </div>
          <div class="social-links">
            <a href="https://t.me/Chugundyrka" target="_blank" class="telegram-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="12" cy="12" r="12" fill="#0088cc"/>
                  <path d="M17.55 6.45C17.85 6.3 18.15 6.6 18.05 6.95L15.75 15.45C15.65 15.8 15.3 15.9 15.05 15.75L12.55 14.05L11.45 15.05C11.35 15.15 11.2 15.25 11 15.2L11.1 12.65L15.6 8.9C15.8 8.75 15.6 8.5 15.35 8.65L9.1 12.15L6.7 11.35C6.35 11.25 6.35 10.8 6.75 10.7L17.55 6.45Z" fill="white"/>
                </svg>
              </a>
          </div><p></p><div class="social-links">
            
            <a href="https://wa.me/+79057007039" target="_blank" class="whatsapp-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="12" cy="12" r="12" fill="#25D366"/>
                  <path d="M16.22 14.28c-.27-.13-1.6-.79-1.84-.88-.24-.09-.41-.13-.58.13-.17.27-.67.88-.82 1.06-.15.18-.3.2-.57.07-.27-.13-1.12-.41-2.13-1.3-.79-.7-1.32-1.57-1.48-1.83-.15-.27-.02-.42.11-.55.11-.11.27-.3.4-.45.13-.15.18-.24.27-.4.09-.18.04-.32-.02-.45-.07-.13-.58-1.42-.8-1.97-.21-.55-.43-.47-.58-.47-.15 0-.32-.02-.5-.02-.18 0-.46.07-.7.34-.24.27-.91.89-.91 2.2 0 1.3.94 2.56 1.07 2.74.13.18 1.85 2.96 4.5 3.94.63.27 1.12.43 1.5.55.63.2 1.2.17 1.65.1.5-.08 1.6-.65 1.82-1.27.22-.63.22-1.17.15-1.27-.08-.09-.23-.15-.5-.27z" fill="white"/>
                </svg>
              </a>
          </div>
        </div>
  
        <nav class="navigation">
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
    color: #f7f6f6; /* Красный цвет для ссылки "Продукция" */
    font-size: 1.6rem; /* Увеличенный размер шрифта */
    font-weight: 600;
    text-decoration: none;
    position: relative; /* Необходимо для позиционирования псевдоэлемента */
  }
  .products-link::before {
    content: '';
    position: absolute;
    left: -20px; /* Расстояние от текста */
    top: 50%;
    transform: translateY(-50%); /* Центрирование по вертикали */
    width: 4px; /* Ширина линии */
    height: 40px; /* Высота линии */
    background-color: red; /* Цвет линии */
  }
  
  .products-link:hover {
    
    color: #c2cdd5; /* Красный цвет для ссылки "Продукция" */

  }
  
  /* Адаптивный стиль для мобильных устройств */
  @media (max-width: 768px) {
    .header-content {
      flex-direction: column;
      align-items: center;
      margin-top: 15px;
    }
  
    .logo {
      text-align: center;
    }
    .logo img{
      display: none;
    }
  
    .contact-info {
      display: none;
    }
  
    .manager-photo {
      display: none;
    }
  
    .phone-contact {
      margin-right: 10px;
    }
  
    .social-links {
      display: flex;
      gap: 1px;
    }
  
    .navigation {
      display: none;
    }
  }
  
  </style>

  