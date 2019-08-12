<template>
<ul class="list-group">
	<li class="list-group-item" v-bind:key="todo.id" v-for="todo in todos">
		<TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
	</li>
</ul>
</template>

<script>
	import TodoItem from './TodoItem';
	export default {
		name: 'Todos',
		components: {
			TodoItem
		},
		props: ["todos"]
	}
</script>

<style scoped>
	
</style>