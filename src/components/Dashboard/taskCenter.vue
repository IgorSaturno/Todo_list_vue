<script setup>
import { ref } from 'vue';
import pageTtile from '../Page/pageTtile.vue';
import DeleteIcon from '@mui/icons-material/Delete';

    let id = 0;

    const newTodo = ref('')
    const todos = ref([])

function addTodo() {
    todos.value.push({ id: id++, text: newTodo.value })
    newTodo.value = ''
}

function removeTodo(todo) {
    todos.value = todos.value.filter((t) => t !== todo)
}

const checked = ref(true)
</script>

<template>
    <div id="todolist">
        <div class="title">
            <pageTtile msg="TodoList Vue"/>
        </div>
        <form @submit.prevent="addTodo">
            <input v-model="newTodo">
            <button>Add Todo</button>
        </form>
        <ul>
            <li v-for="todo in todos" :key="todo.id">
                {{ todo.text }}
                <button @click="removeTodo(todo)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<style scoped>
    #todolist {
        margin: 4rem auto;
        padding: 2rem 3rem 3rem;
        max-width: 500px;
        border-style: solid;
        border-color: hsla(160, 100%, 37%, 1);
        border-radius: 1rem;
    }

    #todolist .title {
        margin-bottom: 1rem;
    }

    form input {
        flex-grow: 1;
        border: none;
        background: white;
        padding: 0 1.5rem;
        font-size: initial;
        margin-bottom: 1rem;
    }

    form button {
        padding: 0 1.3rem;
        border: none;
        background: hsla(160, 100%, 37%, 1);
        color: white;
        text-transform: uppercase;
        font-weight: bold;
        border: 1px solid white;
        margin-left: 5px;
        cursor: pointer;
    }

    form input,
    form button {
        height:2rem;
    }

    
    
</style>