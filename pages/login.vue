<template>
	<div class="auth-page">
	  <h2>Вход</h2>
	  <form @submit.prevent="login">
		<div class="form-group">
		  <label for="email">Email:</label>
		  <input
			v-model="email"
			type="email"
			id="email"
			required
			placeholder="Введите email"
		  />
		</div>
		<div class="form-group">
		  <label for="password">Пароль:</label>
		  <input
			v-model="password"
			type="password"
			id="password"
			required
			placeholder="Введите пароль"
		  />
		</div>
		<button type="submit" class="auth-button">Войти</button>
	  </form>
	  <p>
		Нет аккаунта?
		<NuxtLink to="/register">Зарегистрироваться</NuxtLink>
	  </p>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		email: '',
		password: ''
	  }
	},
	methods: {
	  login() {
		const user = JSON.parse(localStorage.getItem('user'))
		if (user && user.email === this.email && user.password === this.password) {
		  alert('Вход выполнен успешно!')
		  this.$router.push('/')
		} else {
		  alert('Неверный email или пароль')
		}
	  }
	}
  }
  </script>
  
  <style scoped>
  @import '~/assets/css/auth.css';
  </style>