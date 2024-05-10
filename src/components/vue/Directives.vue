<script setup>
import { ref } from 'vue';

const users = ["Pepe", "Juana", "Lola", "Titan"]
const isChecked = ref(true);
</script>

<template>

    <ul>
        <li v-for="(user, index) in users" :key="index">{{ index }} {{ user }}</li>
    </ul>

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
    <input type="text" placeholder="">
</template>

