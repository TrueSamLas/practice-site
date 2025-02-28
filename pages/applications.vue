<template>
	<div class="applications-page">
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
  .applications-page {
	padding: 20px;
	max-width: 1200px;
	margin: 0 auto;
  }
  
  h2 {
	font-size: 28px;
	color: #333;
	margin-bottom: 10px;
	text-align: center;
  }
  
  p {
	font-size: 18px;
	color: #666;
	margin-bottom: 30px;
	text-align: center;
  }
  
  .issues-grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); /* Адаптивные колонки */
	gap: 20px; /* Расстояние между заявками */
	padding: 20px;
	background-color: #f9f9f9; /* Легкий фон для контейнера */
	border-radius: 12px; /* Скругленные углы */
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); /* Тень */
  }
  
  @media (max-width: 768px) {
	.issues-grid {
	  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); /* Две колонки на планшетах */
	}
  }
  
  @media (max-width: 480px) {
	.issues-grid {
	  grid-template-columns: 1fr; /* Одна колонка на мобильных устройствах */
	}
  }
  </style>