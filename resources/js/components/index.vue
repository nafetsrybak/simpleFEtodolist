<template>
    <div class="container-fluid">
        <Header />
        <div class="container">
            <div class="row justify-content-center">
                <AddTodo v-on:add-todo="addTodo"/>
            </div>
            <div class="row justify-content-center">
                <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
            </div>
        </div>
    </div>
</template>

<script>
    import Todos from './Todos';
    import AddTodo from './AddTodo';
    import Header from './layouts/Header';
    export default {
        mounted() {
            console.log('Component mounted.')
        },
        components: {
            Todos,
            Header,
            AddTodo
        },
        data(){
            return {
                todos: [
                ]
            }
        },
        methods: {
            deleteTodo(id){
                this.todos = this.todos.filter(todo => todo.id != id);
            },
            addTodo(newTodo){
                this.todos = [...this.todos, newTodo];
            }
        }
    }
</script>

<style>
    .container-fluid{
        padding: 0;
    }
    .container{
        padding-top: 15px;
    }
</style>
