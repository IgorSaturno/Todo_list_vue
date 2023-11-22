<script setup>
import { ref } from 'vue';
import pageTtile from '../Page/pageTtile.vue';

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

</script>

<template>
    <div id="todolist">
        <div class="title">
            <pageTtile msg="TodoList Vue"/>
        </div>
        <form @submit.prevent="addTodo">
            <input v-model="newTodo" required>
            <button>Add Todo</button>
        </form>
        <div class="list"> 
            <li v-for="todo in todos" :key="todo.id">
                <input class="checkbox" type="checkbox" v-model="todo.completed" />
                <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
                
                <button class="delete" @click="removeTodo(todo)">delete</button>
            </li>
        </div>
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
        margin-left: 1.5rem;
        cursor: pointer;
    }

    form input,
    form button {
        height:2rem;
    }

    div .list {
       display: flex;
       align-items: flex-start;
       flex-flow: column;
    }

    .checkbox {
        margin-right: 8px;
    }

    li {
        list-style: none;
        color:hsla(160, 100%, 37%, 1);
        padding: 10px;
        border: 1px solid hsla(160, 100%, 37%, 1);
        /* min-width: 25rem; */
    }
    .completed {
        text-decoration: line-through;
    }

    button.delete {
        margin-left: 8px;
        cursor: pointer;
    }

</style>