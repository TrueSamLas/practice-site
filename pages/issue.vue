<template>
	<div class="issue">
	  <img :src="image" alt="Заявка" class="issue-image" />
	  <p class="category">Категория: {{ category }}</p>
	  <p :class="['status', statusClass]">Статус: {{ status }}</p>
	</div>
  </template>
  
  <script>
  export default {
	name: 'Issue',
	props: {
	  image: String,
	  category: String,
	  status: String
	},
	computed: {
	  statusClass() {
		return {
		  'status-resolved': this.status === 'Решено',
		  'status-pending': this.status === 'Не проверено',
		  'status-rejected': this.status === 'Отклонено'
		};
	  }
	}
  }
  </script>
  
  <style scoped>
  .issue {
	background-color: white;
	border: 1px solid #e0e0e0; /* Легкая рамка */
	border-radius: 8px; /* Скругленные углы */
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); /* Тень */
	transition: transform 0.2s, box-shadow 0.2s;
  }
  
  .issue:hover {
	transform: translateY(-5px); /* Эффект при наведении */
	box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
  }
  
  .issue-image {
	width: 100%;
	max-width: 100%;
	height: auto;
	border-radius: 8px; /* Скругленные углы для изображения */
  }
  
  .category {
	font-weight: bold;
	color: #4CAF50; /* Зеленый цвет для категории */
	margin: 10px 0 5px;
  }
  
  .status {
	font-style: italic;
	margin: 0;
  }
  
  .status-resolved {
	color: green;
  }
  
  .status-pending {
	color: orange;
  }
  
  .status-rejected {
	color: red;
  }
  </style>