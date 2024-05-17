<script setup>

import { ref } from 'vue'

const todos = ref([]);
const todo = ref('')

const age = 14;

const countries = ref(["Colombia", "Venezuela", "Puerto Rico", "Dominicana"]);

const isChecked = ref(true);

const isOpen = ref(false)
const buttonClass = ref('bg-blue-500 text-white')
const buttonText = ref('Mostrar opciones')

const objetos = ref([{code:'192205', name:'Charis'}, {code:'192203', name:'Guevara'}, {code:'192222', name:'Mamian'} ])

const colortext = ref('text-red')
const hasError = ref(true);







function toggleDropdown() {
  isOpen.value = !isOpen.value
  if (isOpen.value) {
    buttonClass.value = 'bg-red-500 text-white'
    buttonText.value = 'Ocultar opciones'
  } else {
    buttonClass.value = 'bg-blue-500 text-white'
    buttonText.value = 'Mostrar opciones'
  }
}

function add () {
    todos.value.unshift(todo.value)
    todo.value= ''
}
    

</script>

<template>

     <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <button @click="toggleDropdown":class="buttonClass"class="px-4 py-2 rounded focus:outline-none">{{ buttonText }}</button>
    <div v-if="isOpen">
      <div class=" mt-1 px-1">
        <p class="block px-4 py-2 text-sm text-gray-700  mt-1 bg-violet-300 rounded">Opción 1</p>
        <p class="block px-4 py-2 text-sm text-gray-700  mt-1 bg-violet-300 rounded">Opcion 2</p>
        <p class="block px-4 py-2 text-sm text-gray-700  mt-1 bg-violet-300 rounded">Opción 3</p>
      </div>
    </div>
  </div>


    <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
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


    <div class=" px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <input type="checkbox" id="check" v-model="isChecked">
    <label for="check">Pinchame</label>
    <div class=" bg-blue-400 text-white rounded py-1 px-2" :class="{' bg-orange-500':isChecked}">
        Este es un mensaje 
    </div>
    <div v-show="false"> 
        Este es un mensaje que podria ocultar 
    </div>
    <div v-if ="isChecked"> 
        Este es un mensaje que podria ocultar 
    </div>
    <div v-else>
        Es no se ve porque no cumplió la condición de if 
    </div>
    </div>



    <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <div v-if="age >= 18">
            Usted es mayor de edad
        </div>
        <div v-else> Usted es menor de edad</div>
    </div>



    <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <ul>
            <li v-for="(contry, index) in countries" :key="index">{{ contry }}</li>
        </ul>
    </div>

    <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <ul>
            <li v-for="(objeto, index) in objetos" :key="objetos">{{ objeto.name }} {{ objeto.code }}</li>
        </ul>
    </div>

    <div class="px-5 py-6 rounded shadow bg-slate-200 max-w-96 mx-auto  mt-10">
        <p v-bind:class="{'danger' : hasError}">Este mensaje se ha enviado saticfactoriamente</p>
    </div>
<!--PAra que se vean los numeros es la etiqueta index cuando hay valores iguales  -->
   
</template>

<style>
.danger{
    color: rgb(255, 0, 0);
}
</style>