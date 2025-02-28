<template>
	<div class="profile-page">
	  <h2>Личный кабинет</h2>
	  <div class="issues-grid">
		<Issue
		  v-for="(issue, index) in userIssues"
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
	  userIssues() {
		// Здесь можно добавить логику для фильтрации заявок по пользователю
		return JSON.parse(localStorage.getItem('issues')) || []
	  }
	}
  }
  </script>
  
  <style scoped>
  .profile-page {
	max-width: 1200px;
	margin: 50px auto;
	padding: 20px;
  }
  
  h2 {
	text-align: center;
	margin-bottom: 20px;
	font-size: 28px;
	color: #333;
  }
  
  .issues-grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	gap: 20px;
  }
  </style>