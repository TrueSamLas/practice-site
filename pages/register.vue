<template>
	<div class="auth-page">
	  <h2>Регистрация</h2>
	  <form @submit.prevent="register">
		<div class="form-group">
		  <label for="username">Имя пользователя:</label>
		  <input
			v-model="username"
			type="text"
			id="username"
			required
			placeholder="Введите имя пользователя"
		  />
		</div>
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
		<button type="submit" class="auth-button">Зарегистрироваться</button>
	  </form>
	  <p>
		Уже есть аккаунт?
		<NuxtLink to="/login">Войти</NuxtLink>
	  </p>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		username: '',
		email: '',
		password: ''
	  }
	},
	methods: {
	  register() {
		const user = {
		  username: this.username,
		  email: this.email,
		  password: this.password
		}
		localStorage.setItem('user', JSON.stringify(user))
		alert('Регистрация прошла успешно!')
		this.$router.push('/')
	  }
	}
  }
  </script>
  
  <style scoped>
  @import '~/assets/css/auth.css';
  </style>