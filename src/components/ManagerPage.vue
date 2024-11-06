<template>
    <div class="manage-page">
      <div class="manager-info">
        <img :src="manager.photo" alt="Фото менеджера" class="manager-photo" />
        <div class="manager-details">
          <h1>{{ manager.name }}</h1>
          <p>{{ manager.description }}</p>
          <ul class="manager-stats">
            <li v-for="(stat, index) in manager.stats" :key="index">
              <strong>{{ stat.value }}</strong> {{ stat.label }}
            </li>
          </ul>
          <button @click="scheduleCall" class="call-button">Запланировать звонок</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ManagePage',
    data() {
      return {
        manager: {
          name: 'Иван Иванов',
          photo: require('@/assets/img/photo_manager.jpg'),
          description: 'Профессиональный менеджер с более чем 12-летним опытом в сфере продаж.',
          stats: [
            { value: '12', label: 'лет на рынке' },
            { value: '1000+', label: 'клиентов' },
            { value: '5000+', label: 'успешных заказов' },
          ],
        },
      };
    },
    methods: {
      scheduleCall() {
        alert('Запрос на звонок отправлен!');
      },
    },
  };
  </script>
  
  <style scoped>
  .manage-page {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 40px;
  }
  
  .manager-info {
    display: flex;
    background-color: #f7f7f7;
    border-radius: 10px;
    padding: 20px;
    max-width: 1200px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  
  .manager-photo {
    width: 250px;
    height: 250px;
    border-radius: 50%;
    object-fit: cover;
    margin-right: 20px;
  }
  
  .manager-details {
    flex: 1;
  }
  
  h1 {
    margin: 0;
    font-size: 24px;
    color: #333;
  }
  
  p {
    margin: 10px 0;
    color: #666;
  }
  
  .manager-stats {
    list-style: none;
    padding: 0;
    margin: 20px 0;
    display: flex;
    gap: 20px;
  }
  
  .manager-stats li {
    font-size: 16px;
    color: #333;
  }
  
  .call-button {
    padding: 10px 20px;
    background-color: #007bff;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .call-button:hover {
    background-color: #0056b3;
  }
  </style>
  