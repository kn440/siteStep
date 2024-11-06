<template>
    <div class="product-page">
      <!-- Заголовок продукта -->
      <div class="product-header">
        <h1>{{ product.name }}</h1>
        <p class="product-description">{{ product.description }}</p>
        <a :href="product.certificateUrl" class="download-link" download>Скачать сертификат</a>
      </div>
  
      <div class="content-section">
        <!-- Левая колонка: Минимальная покупка и информация о скидках и доставке -->
        <div class="info-section">
          <h2>Стоимость продукции</h2>
          <div class="info-content">
            <div class="purchase">
              <p><strong>Минимальная покупка:</strong></p>
              <p>4 бутыли,</p> <p> <strong>стоимость:</strong> 796 руб. (199 руб. за одну штуку)</p>
            </div>
            <div class="discounts-section">
                <h3 class="discounts-title">Скидки:</h3>
                <ul class="discounts-list">
                  <li>от 10 бутылей — 1400 руб. (140 руб. за одну штуку)</li>
                  <li>от 50 бутылей — 6750 руб. (135 руб. за одну штуку)</li>
                </ul>
              </div>
            <div class="discounts">
              <strong>Варианты доставки:</strong>
              <ul>
                <li>Самовывоз — бесплатно</li>
                <li>Доставка в черте города Одинцово — 300 руб.</li>
                <li>Доставка за городом — 25 руб./км</li>
              </ul>
            </div>
          </div>
        </div>
      
        <!-- Правая колонка: Калькулятор предварительного расчета -->
        <div class="calculator-section">
          <h2>Предварительный расчет</h2>
          <div class="calculator">
            <label>Количество бутылей:
              <input type="number" v-model.number="quantity" min="4" />
            </label>
            <label>Примерное расстояние в километрах от Одинцово:
              <input type="number" v-model.number="distance" min="0" />
            </label>
          </div>
      
          <!-- Результаты расчета -->
          <div class="calculation-result">
            <p>Стоимость продукции: <strong>{{ productCost }} руб.</strong></p>
            <p>Стоимость доставки: <strong>{{ deliveryCost }} руб.</strong></p>
            <p><strong>Итоговая стоимость: {{ totalCost }} руб.</strong></p>
          </div>
        </div>
      </div>
      
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductsPage',
    data() {
      return {
        product: {
          name: 'Незамерзающая жидкость SuperFreeze',
          description: 'Высококачественная незамерзающая жидкость для автомобилей, предназначенная для использования при низких температурах до -30 по Цельсию. Обладает отличными моющими свойствами и обеспечивает безопасное использование. Продукция разлита в 5 литровые бутыли (4,85 литра)',
          certificateUrl: '/path/to/certificate.pdf',
          purchaseOptions: [
            { id: 1, amount: 4, price: 796, one: 199 },
            { id: 2, amount: 10, price: 1400, one: 140 },
            { id: 3, amount: 50, price: 6750, one: 135 },
          ],
         
        },
        quantity: 4,
        distance: 0,
        productCost: 0,
        deliveryCost: 0,
        totalCost: 0,
      };
    },
    watch: {
      quantity: 'calculateCost',
      distance: 'calculateCost',
    },
    methods: {
      
        calculateCost() {
            let costPerBottle;
    
            if (this.quantity < 4) {
          // Если количество меньше 4, то стоимость 0 или сообщение об ошибке
          return 0; // Или можно показать сообщение о минимальной покупке
            } else if (this.quantity >= 4 && this.quantity < 10) {
          costPerBottle = 199; // Цена за бутылку от 4 до 10
            } else if (this.quantity >= 10 && this.quantity < 50) {
              costPerBottle = 140; // Цена за бутылку от 10 до 50
            } else {
              costPerBottle = 135; // Цена за бутылку больше 50
            }

            this.productCost = this.quantity * costPerBottle; // Расчет общей стоимости
            this.calculateDeliveryCost(); // Вызываем метод для расчета стоимости доставки
        },

  calculateDeliveryCost() {
    // Примерный расчет стоимости доставки
    if (this.distance <= 1) {
      this.deliveryCost = 300; // Доставка до 10 км
    } else {
      this.deliveryCost = 300 + (this.distance - 10) * 25; // Доставка свыше 10 км
    }

    this.totalCost = this.productCost + this.deliveryCost; // Общая стоимость
  }
},


    mounted() {
      this.calculateCost(); // Инициализировать расчет при загрузке
    },
  };
  </script>
  
  <style scoped>
  .product-page {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
    color: #333;
  }
  
  .product-header {
    text-align: center;
    margin-bottom: 10px;
  }
  
  .product-header h1 {
    font-size: 2.2em;
    font-weight: bold;
    margin-bottom: 0.5em;
  }
  
  .product-description {
    
    margin-bottom: 1em;
    color: #555;
    text-align: justify;
      font-size: 1.25rem;
      line-height: 1.6;
      
    
  }
  
  .download-link {
    color: #007bff;
    font-weight: 600;
    text-decoration: none;
    border-bottom: 2px solid #007bff;
    transition: color 0.3s, border-bottom-color 0.3s;
  }
  
  .download-link:hover {
    color: #0056b3;
    border-bottom-color: #0056b3;
  }
  
  .content-section {
    display: flex;
    justify-content: space-between; /* Размещение колонок по горизонтали */
    gap: 20px; /* Промежуток между колонками */
    margin: 20px 0; /* Отступы сверху и снизу */
  }
  
  .info-section {
    flex: 1; /* Одинаковая ширина для колонок */
    background: #f9f9f9; /* Светлый фон */
    padding: 20px; /* Отступы внутри колонок */
    border-radius: 10px; /* Сглаженные углы */
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1); /* Тень для отделения от фона */
  }
  
  h2 {
    text-align: center; /* Заголовок по центру */
    margin-bottom: 15px; /* Отступ снизу */
  }
  
  .info-content {
    display: flex;
    flex-direction: column;
    gap: 5px; /* Расстояние между элементами */
  }
  
  

  .discounts {
    background-color: #e6ffe6; /* Светло-зелёный фон */
    padding: 10px;
    border-radius: 8px;
    border: 2px solid #66cc66; /* Насыщенный зелёный ободок */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    margin: 10px auto;
  }
  
  .discounts strong {
    font-size: 1.2rem;
    color: #4d8f4d; /* Темный оттенок для текста заголовка */
  }
  
  .discounts ul {
    margin-top: 10px;
    padding-left: 20px;
    color: #4d8f4d; /* Темный зеленый для текста списка */
  }
  
  .discounts li {
    margin-bottom: 8px;
  }
  

  .purchase {
    max-width: 400px;
    margin: 20px auto;
    padding: 20px;
    background-color: #ffe6e6;
    border: 2px solid #ffcccc;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    font-size: 1em;
    color: #333;
    text-align: center;
  }
  
  .purchase strong {
    display: block;
    font-size: 1.2em;
    color: #e67300;
    font-weight: bold;
  }
  
  .purchase p {
    font-size: 1.1em;
    color: #444;
    margin: 0;
  }
  
 

  
  
  


  .calculator-section {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f9f9f9;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .calculator-section h2 {
    font-size: 1.5em;
    margin-bottom: 20px;
    color: #333;
    text-align: center;
  }
  
  .calculator {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  
  .calculator label {
    display: flex;
    flex-direction: column;
    font-size: 1em;
    color: #555;
  }
  
  .calculator input[type="number"] {
    padding: 10px;
    margin-top: 5px;
    font-size: 1em;
    border: 1px solid #ccc;
    border-radius: 4px;
    transition: border-color 0.3s ease;
  }
  
  .calculator input[type="number"]:focus {
    border-color: #007bff;
    outline: none;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.2);
  }
  
  
 
  .calculation-result {
    max-width: 400px;
    margin: 20px auto 0;
    padding: 20px;
    background-color: #eef2f7;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-size: 1em;
    color: #333;
  }
  
  .calculation-result p {
    font-size: 1em;
    margin: 10px 0;
    color: #444;
  }
  
  .calculation-result p strong {
    color: #007bff;
    font-weight: bold;
  }
  
  .calculation-result p:last-of-type {
    font-size: 1.2em;
    margin-top: 15px;
    color: #222;
  }
  .discounts-section {
    background-color: #fff9e6; /* Светлый желтоватый фон */
    border: 2px solid #ffd966;;
    padding: 5px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    margin: 0px auto; /* Центрирование блока */
  }
  
  .discounts-title {
    font-size: 1.5rem;
    font-weight: bold;
    color: #333;
    
    text-align: center;
  }
  
  .discounts-list {
    list-style-type: none;
    padding-left: 0;
    font-size: 1.1rem;
    line-height: 1.6;
    color: #555;
  }
  
  .discounts-list li {
    margin-bottom: 5px;
    font-weight: 500;
  }

  @media (max-width: 480px) {
    .content-section {
      margin: 0 auto; /* Центрирует блок по горизонтали */
  padding: 0;
      flex-direction: column; /* Меняем направление на колонку */
    }
    .info-section {
      
      background: #f9f9f9; /* Светлый фон */
      padding: 20px; /* Отступы внутри колонок */
      border-radius: none; /* Сглаженные углы */
      box-shadow: none; /* Тень для отделения от фона */
    }
  
    
    .info-section,
    .calculator-section {
      width: 100%; /* Делаем блоки на всю ширину */
      margin-bottom: 15px; /* Добавляем отступ снизу */
    }
  }
  
  
</style>  