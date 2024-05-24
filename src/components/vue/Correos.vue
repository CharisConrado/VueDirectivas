<script setup>
    import { ref } from 'vue';
    import { defineProps } from 'vue';
    let props = defineProps({
        title: String,
        text: String,
        time: String
    })


    let borde = ref(true);
    let borde2 = ref(false);
    let negrilla = ref(true);
    let leido = ref('');

    function Marcar(){
        if(borde.value != false){
            borde.value = false;
            borde2.value = true;
            negrilla.value = false;
            leido.value = '';
        }else{
            borde.value = true;
            borde2.value = false;
            leido.value = '';
        }
        
    }
    function Sobre(){
        if(negrilla.value != false){
            leido.value = 'Marcar como leido';
        }
        
    }
    function fuera(){
        leido.value = '';
    }

</script>

<template>
    <div 
    :class="{'hover:border':borde,
            'border-4':borde2}"
    class="flex m-4 bg-white p-4 hover:border-blue-400 border-blue-400 max-w-96 font-sans"
     @click="Marcar" @mouseover="Sobre" @mouseleave="fuera">
        <div>
            Icon
        </div>
        <div class="grid text-left mx-4">
            <h6
            :class="{'font-bold':negrilla}">{{ title }}</h6>
            <h6>{{ text }}</h6>
            <p class="text-zinc-400 text-xs">{{ time }}</p>
        </div>
        <div 
        class="text-right text-zinc-400 text-xs  ml-6">
            {{ leido }}
        </div>
    </div>
</template>