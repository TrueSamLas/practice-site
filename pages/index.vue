<template>
	<div>
	  <div class="banner">
		<div class="banner-content">
		  <h1>Сделаем наш город лучше!</h1>
		  <p>Сломанные детские площадки?</p>
		  <p>Старые здания?</p>
		  <p>Испорченные дороги?</p>
		  <NuxtLink to="/create-issue" class="banner-button">Оставить заявку</NuxtLink>
		</div>
	  </div>
	  <div class="container">
		<div class="issues">
		  <h2>Заявки</h2>
		  <p>Количество выполненных заявок: {{ resolvedIssuesCount }}</p>
		  <div class="issues-grid">
			<Issue
			  v-for="(issue, index) in issues"
			  :key="index"
			  :image="issue.image"
			  :category="issue.category"
			  :description="issue.description"
			  :status="issue.status"
			/>
		  </div>
		</div>
	  </div>
	</div>
  </template>
  
  <script>
  import Issue from '../pages/issue.vue'
  
  export default {
	components: {
	  Issue
	},
	computed: {
	  issues() {
		return JSON.parse(localStorage.getItem('issues')) || []
	  },
	  resolvedIssuesCount() {
		return this.issues.filter(issue => issue.status === 'Решено').length
	  }
	}
  }
  </script>
  
  <style scoped>
  .banner {
	background: url("../assets/banner.jpg");
	background-repeat: no-repeat;
	background-size: cover;
	color: white;
	padding: 60px 20px;
	text-align: center;
	margin-bottom: 40px;
  }
  
  .banner-content {
	max-width: 800px;
	margin: 0 auto;
  }
  
  .banner h1 {
	font-size: 36px;
	margin-bottom: 20px;
  }
  
  .banner p {
	font-size: 20px;
	margin: 10px 0;
  }
  
  .banner-button {
	display: inline-block;
	margin-top: 20px;
	padding: 12px 30px;
	background-color: #ffdfb1;
	background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, #a2dec2 100%), #ffdfb1;
	color: white;
	text-decoration: none;
	border-radius: 20px;
	font-size: 18px;
	font-weight: bold;
	transition: transform 0.3s, box-shadow 0.3s;
  }
  
  .banner-button:hover {
	transform: translateY(-2px);
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
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
	grid-template-columns: repeat(3, 1fr);
	gap: 20px;
  }
  </style>