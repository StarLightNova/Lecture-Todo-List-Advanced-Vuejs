<template>
    <h1>I AM TODO LIST</h1>
    <form>
        <label for='newTodoInput'>Add a new TODO:</label>
        <input id='newTodoInput' type='text' v-model.trim='newTodoInput' />
        <button @click.prevent='addTodo' type='submit'>ADD</button>
    </form>
    <ul>
        <li v-for='todo in todos' :key='todo'>
            <Todo :propName=todo.name
                :propId=todo.id
                :propIsChecked=todo.isChecked
                @update-check='updateTodoCheck'
                @delete-todo='deleteTodo'
            />
        </li>
        <li v-for='todo in todos' :key='todo'>
            ID: {{todo.id}} <br/>
            Name: {{todo.name}} <br/>
            isChecked: {{todo.isChecked}}
        </li>
    </ul>
</template>

<script>
import Todo from './Todo.vue'

export default {
    name: 'TodoList',
    components:{
        Todo,
    },
    emits: ['update-check', 'delete-todo'],
    data(){
        return{ 
            newTodoInput: '',
            idCounter: 0,
            todos: [],
        }
    },
    methods:{
        addTodo(){
            this.todos.push(
                {
                    id: this.idCounter++,
                    name: this.newTodoInput,
                    isChecked: false,
                }
            );
            this.newTodoInput = '';
        },
        deleteTodo(todoId){
            this.todos.splice(
                this.todos.indexOf(
                    this.todos.find(el => el.id === todoId)
                ), 1
            );
        },
        updateTodoCheck(todoId){
            this.todos.find(el => el.id === todoId).isChecked = !this.todos.find(el => el.id === todoId).isChecked
        }
    }
}
</script>