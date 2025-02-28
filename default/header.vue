<template>
	<header>
	  <div class="header-content">
		<div class="nav-left">
		  <NuxtLink to="/" class="nav-text"><b>Главная</b></NuxtLink>
		  <NuxtLink to="/applications" class="nav-text"><b>Заявки</b></NuxtLink>
		</div>
		<div class="logo">
		  <NuxtLink to="/">
			<img src="~/assets/logo.png" alt="Логотип" />
		  </NuxtLink>
		</div>
		<div class="nav-right">
		  <NuxtLink to="/login" class="nav-button"><b>Вход</b></NuxtLink>
		  <NuxtLink to="/register" class="nav-button"><b>Регистрация</b></NuxtLink>
		  <NuxtLink to="/admin" class="nav-button"><b>Админ</b></NuxtLink>
		</div>
	  </div>
	</header>
  </template>
  
  <script>
  export default {
	name: 'AppHeader'
  }
  </script>
  
  <style scoped>
  header {
	background-color: #9CCBB5;
	color: white;
	padding: 20px;
	text-align: center;
  }
  
  .header-content {
	display: flex;
	justify-content: space-between;
	align-items: center;
	max-width: 1200px;
	margin: 0 auto;
  }
  
  .nav-left, .nav-right {
	display: flex;
	gap: 20px;
	flex: 1;
  }
  
  .nav-left {
	justify-content: flex-start;
  }
  
  .nav-right {
	justify-content: flex-end;
  }
  
  .logo {
	flex: 0 0 auto; 
  }
  
  .logo img {
	height: 70px;
	transition: transform 0.2s; 
  }
  
  .logo img:hover {
	transform: scale(1.05);
  }
  
  .nav-text {
	color: white;
	text-decoration: none;
	font-size: 16px;
	font-weight: bold;
	transition: color 0.3s;
  }
  
  .nav-text:hover {
	color: #f0f0f0;
  }
  
  .nav-button {
	background: #ffdfb1;
	background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, #a2dec2 100%), #ffdfb1;
	color: white;
	text-decoration: none;
	padding: 10px 30px;
	border: none;
	border-radius: 20px;
	transition: background-color 0.3s, color 0.3s;
  }
  
  .nav-button:hover {
	background-color: white;
	color: #555555;
  }
  </style>
  