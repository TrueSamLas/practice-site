<template>
	<div class="admin-page">
	  <h2>Админ панель</h2>
	  <div class="issues-list">
		<div v-for="(issue, index) in issues" :key="index" class="issue-card">
		  <div class="issue-info">
			<p><strong>Категория:</strong> {{ issue.category }}</p>
			<p><strong>Статус:</strong> {{ issue.status }}</p>
		  </div>
		  <div class="issue-actions">
			<select v-model="issue.status" @change="updateStatus(index)">
			  <option value="Решено">Решено</option>
			  <option value="Не проверено">Не проверено</option>
			  <option value="Отклонено">Отклонено</option>
			</select>
			<button @click="editIssue(index)" class="edit-button">Редактировать</button>
			<button @click="deleteIssue(index)" class="delete-button">Удалить</button>
		  </div>
		</div>
	  </div>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		issues: JSON.parse(localStorage.getItem('issues')) || [
		  { category: 'Дороги', status: 'Решено' },
		  { category: 'Дороги', status: 'Не проверено' },
		  { category: 'Дороги', status: 'Отклонено' }
		]
	  }
	},
	methods: {
	  updateStatus(index) {
		// Сохраняем изменения в localStorage
		localStorage.setItem('issues', JSON.stringify(this.issues))
		alert(`Статус заявки изменен на: ${this.issues[index].status}`)
	  },
	  editIssue(index) {
		const updatedCategory = prompt('Введите новую категорию:', this.issues[index].category)
		if (updatedCategory) {
		  this.issues[index].category = updatedCategory
		  localStorage.setItem('issues', JSON.stringify(this.issues))
		  alert('Категория заявки обновлена')
		}
	  },
	  deleteIssue(index) {
		if (confirm('Вы уверены, что хотите удалить эту заявку?')) {
		  this.issues.splice(index, 1)
		  localStorage.setItem('issues', JSON.stringify(this.issues))
		  alert('Заявка удалена')
		}
	  }
	}
  }
  </script>
  
  <style scoped>
  .admin-page {
	max-width: 800px;
	margin: 50px auto;
	padding: 20px;
	background-color: #f9f9f9;
	border-radius: 12px;
	box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  }
  
  h2 {
	text-align: center;
	margin-bottom: 20px;
	font-size: 28px;
	color: #333;
  }
  
  .issues-list {
	display: flex;
	flex-direction: column;
	gap: 20px;
  }
  
  .issue-card {
	display: flex;
	justify-content: space-between;
	align-items: center;
	padding: 20px;
	background-color: white;
	border-radius: 8px;
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .issue-info {
	flex: 1;
  }
  
  .issue-info p {
	margin: 0;
	font-size: 16px;
	color: #555;
  }
  
  .issue-actions {
	display: flex;
	gap: 10px;
  }
  
  select {
	padding: 8px;
	border: 1px solid #ddd;
	border-radius: 4px;
	font-size: 14px;
  }
  
  .edit-button, .delete-button {
	padding: 8px 16px;
	border: none;
	border-radius: 4px;
	font-size: 14px;
	cursor: pointer;
	transition: background-color 0.3s;
  }
  
  .edit-button {
	background-color: #4CAF50;
	color: white;
  }
  
  .edit-button:hover {
	background-color: #45a049;
  }
  
  .delete-button {
	background-color: #f44336;
	color: white;
  }
  
  .delete-button:hover {
	background-color: #e53935;
  }
  </style>