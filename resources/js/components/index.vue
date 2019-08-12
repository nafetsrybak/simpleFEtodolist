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
    import axios from 'axios';

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
                const {title, completed} = newTodo;
                axios.post('https://jsonplaceholder.typicode.com/todos', {
                    title,
                    completed
                })
                .then(res => this.todos = [...this.todos, res.data])
                .catch(err => console.log(err));
            }
        },
        created(){
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
            .then(res =>this.todos = res.data)
            .catch(err => console.log(err))
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
