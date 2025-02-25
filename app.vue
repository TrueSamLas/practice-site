<template>
	<div>
	  <!-- Глобальный хедер -->
	  <AppHeader />
  
	  <!-- Основное содержимое страницы -->
	  <NuxtPage />
  
	  <!-- Глобальный футер -->
	  <AppFooter />
	</div>
  </template>
  
  <script>
  import AppHeader from './default/header.vue'
  import AppFooter from './default/footer.vue'
  
  export default {
	components: {
	  AppHeader,
	  AppFooter
	}
  }
  </script>
  
  <style>
  /* Глобальные стили */
  body {
	font-family: Arial, sans-serif;
	margin: 0;
	padding: 0;
	background-color: #f4f4f4;
	color: #333;
  }
  
  .container {
	max-width: 1200px;
	margin: 0 auto;
	padding: 20px;
  }
  </style>