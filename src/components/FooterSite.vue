<template>
    <footer class="footer">
      <!-- <div class="footer-content">
        <div class="contact-info">
          <p>ООО "Незамерзайка"</p>
          <p>Телефон: <a href="tel:+123456789">+1 (234) 567-89</a></p>
          <p>Email: <a href="mailto:info@nezamerzayka.com">info@nezamerzayka.com</a></p>
          <p>Адрес: г. Москва, ул. Примерная, д. 10</p>
        </div>
        <div class="social-links">
          
          <a href="https://facebook.com" target="_blank" aria-label="Facebook">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path d="M22.675 0h-21.35C.6 0 0 .6 0 1.325v21.351C0 23.4.6 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.41c0-3.1 1.894-4.787 4.659-4.787 1.325 0 2.462.099 2.794.143v3.24h-1.917c-1.504 0-1.797.715-1.797 1.762v2.309h3.588l-.467 3.622h-3.121V24h6.116C23.4 24 24 23.4 24 22.676V1.325C24 .6 23.4 0 22.675 0z"/>
            </svg>
          </a>
          
          
          <a href="https://instagram.com" target="_blank" aria-label="Instagram">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 2.163c3.204 0 3.584.012 4.85.07 1.366.062 2.633.33 3.608 1.304.975.975 1.242 2.242 1.304 3.608.058 1.267.07 1.646.07 4.85s-.012 3.584-.07 4.85c-.062 1.366-.33 2.633-1.304 3.608-.975.975-2.242 1.242-3.608 1.304-1.267.058-1.646.07-4.85.07s-3.584-.012-4.85-.07c-1.366-.062-2.633-.33-3.608-1.304-.975-.975-1.242-2.242-1.304-3.608-.058-1.267-.07-1.646-.07-4.85s.012-3.584.07-4.85c.062-1.366.33-2.633 1.304-3.608C5.317 2.493 6.584 2.226 7.95 2.163 9.216 2.105 9.596 2.163 12 2.163m0-2.163C8.691 0 8.271.014 7.002.072 5.571.135 4.229.448 3.129 1.549c-1.1 1.1-1.413 2.442-1.476 3.873C1.941 7.729 1.926 8.148 1.926 12s.014 4.271.072 5.5c.063 1.431.376 2.773 1.477 3.873 1.1 1.1 2.442 1.413 3.873 1.476 1.229.058 1.648.072 5.5.072s4.271-.014 5.5-.072c1.431-.063 2.773-.376 3.873-1.477 1.1-1.1 1.413-2.442 1.476-3.873.058-1.229.072-1.648.072-5.5s-.014-4.271-.072-5.5c-.063-1.431-.376-2.773-1.476-3.873C19.773.448 18.431.135 17 .072 15.771.014 15.352 0 12 0z"/>
              <path d="M12 5.838A6.162 6.162 0 0 0 5.838 12 6.162 6.162 0 0 0 12 18.162 6.162 6.162 0 0 0 18.162 12 6.162 6.162 0 0 0 12 5.838zm0 10.066A3.904 3.904 0 1 1 12 8.096a3.904 3.904 0 0 1 0 7.808zM18.406 4.594a1.44 1.44 0 1 0 0-2.88 1.44 1.44 0 0 0 0 2.88z"/>
            </svg>
          </a>
          
          
          <a href="https://vk.com" target="_blank" aria-label="VK">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 0C5.373 0 0 5.373 0 12c0 6.627 5.373 12 12 12 6.627 0 12-5.373 12-12 0-6.627-5.373-12-12-12zm6.307 17.354h-1.354c-.794 0-1.15-.635-1.895-1.488-.949-.95-1.335-1.068-1.567-1.068-.324 0-.408.113-.408.667v1.275c0 .323-.113.534-.857.534-1.535 0-3.24-1.01-4.432-2.66C7.25 12.276 6.82 10.83 6.82 9.76c0-.324.1-.48.515-.48h1.354c.405 0 .548.227.63.49.364 1.107 1.225 2.27 1.562 2.27.324 0 .245-.453.245-.757v-1.064c-.041-.793.185-1.217.876-1.217h1.192c.245 0 .408.113.445.497.06.67-.153 1.053.268 1.057.324 0 1.172-.61 1.566-.955.405-.355.566-.242.566-.137v1.17c.006.443-.224.51-.535.823-.493.507-.657.682-.657 1.18v.546c0 .245.324.563.657.872.595.57 1.13 1.193 1.57 1.8.163.203.268.36.268.672-.006.285-.216.435-.527.435z"/>
            </svg>
          </a>
        </div>
      </div> -->
      <div class="footer-bottom">
        <p>&copy; 2024 Незамерзайка. Все права защищены.</p>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'FooterSite',
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: #333333;
    color: #ffffff;
    padding: 20px;
    text-align: center;
  }
  
  .footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    max-width: 1200px;
    margin: 0 auto;
    padding-bottom: 10px;
    border-bottom: 1px solid #444444;
  }
  
  .contact-info p {
    margin: 5px 0;
  }
  
  .contact-info a {
    color: #ffffff;
    text-decoration: none;
  }
  
  .contact-info a:hover {
    text-decoration: underline;
  }
  
  .social-links {
    display: flex;
    gap: 15px;
  }
  
  .social-links svg {
    width: 24px;
    height: 24px;
    fill: #ffffff;
    transition: transform 0.3s ease;
  }
  
  .social-links svg:hover {
    transform: scale(1.1);
  }
  
  .footer-bottom {
    margin-top: 10px;
    font-size: 0.9em;
    color: #bbbbbb;
  }
  </style>
  