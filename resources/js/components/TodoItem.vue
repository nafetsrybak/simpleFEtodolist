<template>
	<span v-bind:class="{'list-group-item-success':todo.completed}">
		<input type="checkbox" v-on:change="markComplete">
		{{ todo.title }}
		<button @click="$emit('del-todo', todo.id)" class="btn btn-danger">Delete</button>
	</span>
</template>

<script>
	export default{
		name: 'TodoItem',
		props: ["todo"],
		methods: {
			markComplete(){
				this.todo.completed = !this.todo.completed;
			}
		}
	}
</script>

<style scoped>
	
</style>