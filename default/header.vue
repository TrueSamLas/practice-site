<template>
	<header>
	  <div class="header-content">
		<div class="nav-left">
		  <NuxtLink to="/" class="nav-button"><b>Главная</b></NuxtLink>
		  <NuxtLink to="/applications" class="nav-button"><b>Заявки</b></NuxtLink>
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
	}

	.logo img {
	height: 70px; /* Уменьшена высота логотипа */
	transition: transform 0.2s; /* Анимация при наведении */
	}

	.logo img:hover {
	transform: scale(1.05); /* Увеличение логотипа при наведении */
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