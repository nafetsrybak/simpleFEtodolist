<template>
<form v-on:submit.prevent="addTodo">
	<div class="form-group row">
		<input type="text" v-model="title" name="title" class="form-control" placeholder="Add Todo...">
	</div>
	<div class="form-group row">
		<button class="btn btn-success">Submit</button>
	</div>
</form>
</template>

<script>
	// import uuid from 'uuid';
	export default {
		name: 'AddTodo',
		data(){
			return{
				title: ''
			}
		},
		methods: {
			addTodo(){
				const newTodo = {
					// id: uuid.v4(),
					title: this.title,
					completed: false
				}
				this.$emit('add-todo', newTodo);

				this.title = '';
			}
		}
	}
</script>