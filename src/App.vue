<template>
  <img alt="Vue logo" src="./assets/logo.png">
	<div class="container">
		<form class="formContainer" @submit="handleSubmit">
			<input class="input" type="text" placeholder="Enter Your Todo" v-model="text" />
			<button type="submit">Add</button>
		</form>
		<h3>Your Todos:</h3>
		<ul class="todoItem">
			<li v-for="todo in todos" :key="todo">{{todo}}</li>
		</ul>
	</div>
</template>

<script>
export default {
  name: 'App',
	data () {
		return {
			text: '',
			todos: [],
			handleSubmit(e){
				// this will prevent reloading the page on form submittion
				e.preventDefault();
				// this will check if the text is empty
				if(!this.text) return;
				// finally we add the todo to the todos array and set the text to empty
				this.todos.push(this.text);
				this.text = '';
			}
		}
	},
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container{
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	width: 250px;
	margin: 0 auto;
}

.formContainer {
	margin-bottom: 20px;
	display: flex;
	justify-content: space-between;
}

.formContainer input {
	width: 100%;
	padding: 12px 20px;
	border: 1px solid #ccc;
	border-radius: 4px;
	box-sizing: border-box;
	font-size: 1.2em;
}

.formContainer button {
	display: none;
}

.todoItem{
	width: 100%;
	list-style: none;
	margin: 0 auto;
	padding: 0;
	border-radius: 4px;
	background-color: #f5f5f5;
}

.todoItem li{
	width: 100%;
	margin: 2px auto;
	padding: 8px 0px;
	border: 1px solid #e0e0e0;
	border-radius: 4px;
	background-color: #f5f5f5;
}

</style>
