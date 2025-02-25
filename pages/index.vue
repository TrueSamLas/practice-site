<template>
	<div>
	  <div class="container">
		<div class="issues">
		  <h2>Заявки</h2>
		  <p>Количество выполненных заявок: 999</p>
		  <div class="issues-grid">
			<Issue image="placeholder.jpg" category="Дороги" status="Решено" />
			<Issue image="placeholder.jpg" category="Дороги" status="Решено" />
			<Issue image="placeholder.jpg" category="Дороги" status="Не проверено" />
			<Issue image="placeholder.jpg" category="Дороги" status="Отклонено" />
		  </div>
		</div>
		<a href="#" class="button">Оставить заявку</a>
	  </div>
	  <AppFooter />
	</div>
  </template>
  
  <script>
  import AppHeader from './default/header.vue'
  import AppFooter from './default/footer.vue'
  import Issue from './pages/issue.vue'
  
  export default {
	components: {
	  AppHeader,
	  AppFooter,
	  Issue
	}
  }
  </script>
  
  <style>
  body {
	font-family: Arial, sans-serif;
	margin: 0;
	padding: 0;
	background-color: #f4f4f4;
	color: #333;
  }
  
  .container {
	padding: 20px;
  }
  
  .issues {
	background-color: white;
	padding: 20px;
	margin-bottom: 20px;
	border-radius: 5px;
	box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .issues-grid {
	display: grid;
	grid-template-columns: repeat(3, 1fr); /* Три колонки */
	gap: 20px; /* Расстояние между блоками */
  }
  
  .button {
	background-color: #4CAF50;
	color: white;
	padding: 10px 20px;
	text-align: center;
	text-decoration: none;
	display: inline-block;
	font-size: 16px;
	margin: 10px 0;
	cursor: pointer;
	border-radius: 5px;
  }
  </style>