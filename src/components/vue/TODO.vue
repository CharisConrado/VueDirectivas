<script setup>

import { ref } from 'vue'

const todos = ref(['Estudiar bastante']);
const todo = ref('')

function add () {
    todos.value.unshift(todo.value)
    todo.value= ''
}
function del (){
    todos.value=''
}
</script>

<template>
    <div class=" px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <div > 
            <input v-model="todo" class=" w-4/5 outline-none rounded px-2"/>
            <button @click="add" class="w-1/5 bg-violet-500 text-white text-center rounded">
                +
            </button>
            <button @click="del" class="w-1/5 bg-violet-500 text-white text-center rounded">
                -
            </button>
        </div>
        <div class="mt-3">
            <div v-for="(todo, i) in todos" :key="i" class=" mt-1 px-1 bg-violet-300 rounded"> {{ todo }}</div>
        </div>
    </div>
</template>