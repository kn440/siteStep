<template>
    <div class="product-page">
      <!-- Заголовок продукта -->
      <div class="product-header">
        <h1>{{ product.name }}</h1>
        <p class="product-description">{{ product.description }}</p>
        
      <a :href="product.certificateUrl" class="download-link" download="certificate.jpeg">
        Скачать сертификат
      </a>
    </div>
      <div class="content-section">
        <!-- Левая колонка: Минимальная покупка и информация о скидках и доставке -->
        <div class="info-section">
          <h2>Стоимость продукции</h2>
          <div class="info-content">
            <div class="purchase">
              <p><strong>Минимальная покупка:</strong></p>
              <ul >
                <li>4 бутыли — 796 руб. (199 руб. за одну штуку)</li></ul>
            </div>
            <div class="discounts-section">
              <p><strong>Скидки:</strong></p>
                <ul >
                  <li>от 10 бутылей — 1400 руб. (140 руб. за одну штуку)</li>
                  <li>от 50 бутылей — 6750 руб. (135 руб. за одну штуку)</li>
                </ul>
              </div>
            <div class="discounts">
              <p><strong>Варианты доставки:</strong></p>
              <ul>
                <li>Самовывоз — бесплатно</li>
                <li>Доставка в черте города Одинцово — <strong>300 руб.</strong></li>
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
          name: 'Незамерзающая жидкость  Nord Ultra',
          description: 'Высококачественная незамерзающая жидкость для автомобилей, предназначенная для использования при низких температурах до -30 по Цельсию. Обладает отличными моющими свойствами и обеспечивает безопасное использование. Продукция разлита в 5 литровые бутыли (4,85 литра)',
          certificateUrl: require('@/assets/certificate.jpeg'),
         
         
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
      this.deliveryCost = 300 + (this.distance - 1) * 25; // Доставка свыше 10 км
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
  
 
/* Общие настройки блоков */
.discounts,
.purchase,
.discounts-section {
    font-family: Arial, sans-serif; /* Единый шрифт для всех блоков */
    font-size: 1em; /* Размер шрифта */
    max-width: 400px;
    margin: 10px auto; /* Одинаковый отступ сверху и снизу */
    padding: 15px; /* Одинаковый отступ внутри блоков */
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: left; /* Выравнивание содержимого по левой стороне */
}

/* Индивидуальные цвета блоков */
.discounts {
    background-color: #e6ffe6; /* Светло-зелёный фон */
    border: 2px solid #66cc66; /* Насыщенный зелёный ободок */
    color: #2e7d32; /* Темный зеленый для текста */
}

.purchase {
    background-color: #ffe6e6; /* Светло-розовый фон */
    border: 2px solid #ff9999; /* Темный, но мягкий красный ободок */
    color: #993333; /* Темный текст */
}

.discounts-section {
    background-color: #fff9e6; /* Светлый желтоватый фон */
    border: 2px solid #ffd966; /* Светло-желтый ободок */
    color: #5c4033; /* Темный текст */
}

/* Настройки для списков */
.discounts ul,
.purchase ul,
.discounts-section ul {
    margin: 10px 0 0 20px; /* Отступы: сверху 10px, слева 20px */
    padding: 5px;
    list-style-type: disc; /* Маркер — точки */
    font-size: 1em; /* Размер шрифта */
}

.discounts li,
.purchase li,
.discounts-section li {
    margin-bottom: 8px;
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
 
  
 

  @media (max-width: 480px) {
    

    .content-section {
      display: flex;
      justify-content: space-between;
      flex-direction: column; /* Меняем направление на колонку */
      align-items: flex-start; /* Выровнять блоки по верхнему краю */
      gap: 20px;
      margin: 20px 0;
    }
    
    .info-section,
    .calculator-section {
      flex: 1; /* Одинаковая ширина для колонок */
      padding: 20px; /* Отступы внутри колонок */
      max-width: 400px; /* Ограничение ширины */
      background: #f9f9f9;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
  }
  
  
</style>  