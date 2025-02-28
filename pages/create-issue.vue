<template>
	<div class="create-issue-page">
	  <h2>Создать заявку</h2>
	  <form @submit.prevent="createIssue">
		<div class="form-group">
		  <label for="category">Категория:</label>
		  <select v-model="category" id="category" required>
			<option value="Дороги">Дороги</option>
			<option value="Детские площадки">Детские площадки</option>
			<option value="Здания">Здания</option>
		  </select>
		</div>
		<div class="form-group">
		  <label for="description">Описание:</label>
		  <textarea
			v-model="description"
			id="description"
			required
			placeholder="Опишите проблему"
		  ></textarea>
		</div>
		<div class="form-group">
		  <label for="image">Изображение:</label>
		  <input
			type="file"
			id="image"
			accept="image/*"
			@change="handleImageUpload"
		  />
		</div>
		<button type="submit" class="submit-button">Создать заявку</button>
	  </form>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		category: 'Дороги',
		description: '',
		image: null
	  }
	},
	methods: {
	  handleImageUpload(event) {
		const file = event.target.files[0]
		if (file) {
		  const reader = new FileReader()
		  reader.onload = (e) => {
			this.image = e.target.result
		  }
		  reader.readAsDataURL(file)
		}
	  },
	  createIssue() {
		const newIssue = {
		  category: this.category,
		  description: this.description,
		  image: this.image || 'placeholder.jpg',
		  status: 'Не проверено'
		}
		const issues = JSON.parse(localStorage.getItem('issues')) || []
		issues.push(newIssue)
		localStorage.setItem('issues', JSON.stringify(issues))
		alert('Заявка успешно создана!')
		this.$router.push('/')
	  }
	}
  }
  </script>
  
  <style scoped>
  .create-issue-page {
	max-width: 600px;
	margin: 50px auto;
	padding: 20px;
	background-color: white;
	border-radius: 12px;
	box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  }
  
  h2 {
	text-align: center;
	margin-bottom: 20px;
	font-size: 28px;
	color: #333;
  }
  
  .form-group {
	margin-bottom: 20px;
  }
  
  label {
	display: block;
	margin-bottom: 8px;
	font-weight: 600;
	color: #555;
  }
  
  select, textarea, input[type="file"] {
	width: 95%;
	padding: 12px;
	border: 1px solid #ddd;
	border-radius: 8px;
	font-size: 16px;
	transition: border-color 0.3s, box-shadow 0.3s;
  }
  
  select:focus, textarea:focus, input[type="file"]:focus {
	border-color: #4CAF50;
	box-shadow: 0 0 8px rgba(76, 175, 80, 0.3);
	outline: none;
  }
  
  textarea {
	resize: vertical;
	min-height: 100px;
  }
  
  .submit-button {
	width: 100%;
	padding: 12px;
	background: #ffdfb1;
	background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, #a2dec2 100%), #ffdfb1;
	color: white;
	border: none;
	border-radius: 8px;
	font-size: 16px;
	font-weight: 600;
	cursor: pointer;
	transition: background 0.3s, transform 0.3s;
  }
  
  .submit-button:hover {
	background: #9CCBB5;
	transform: translateY(-2px);
  }
  </style>