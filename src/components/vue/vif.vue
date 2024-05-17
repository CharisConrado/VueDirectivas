<script setup>

import { ref } from 'vue'

let age = 18;
</script>

<template>
    <div v-if="age < 18"> Eres menor de edad </div>
    <div v-else> Eres mayor de edad  </div>
</template>