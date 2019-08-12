<template>
    <div class="container">
        <Header />
        <div class="row justify-content-center">
            <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
        </div>
    </div>
</template>

<script>
    import Todos from './Todos';
    import Header from './layouts/Header';
    export default {
        mounted() {
            console.log('Component mounted.')
        },
        components: {
            Todos,
            Header
        },
        data(){
            return {
                todos: [
                    {
                        id: 1,
                        title: 'Todo one',
                        completed: false
                    },
                    {
                        id: 2,
                        title: "Todo Two",
                        completed: true
                    },
                    {
                        id: 3,
                        title: "Todo Three",
                        completed: false
                    }
                ]
            }
        },
        methods: {
            deleteTodo(id){
                this.todos = this.todos.filter(todo => todo.id != id);
            }
        }
    }
</script>

<style>
    
</style>
