<template>
  <div @click="selectedPlan" class="plan">
    <div class="description">
      <span class="title">
         {{ name }} {{ selected ? '🌟' : '' }}  </span>
    </div>
  </div>
</template>

<script setup>
//import ref fuction 
import { ref } from 'vue';
// Usando macro para definir las props
// definir las props
//define props (['name', 'planIcon']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }
  
 });
//Define event 
const emit = defineEmits(['select']); 
//Variable que permite 
// recordar si el plan ha sido seleccionado 
const selected = ref(false);
//Función que permite cambiar el estado de la variable
// selected
const selectedPlan = () => {
  selected.value = true;
  //Emitir que el evento ha sido seleccionado
  //plan ha sido seleccionado
emit('select', props.name);
};
</script>

<style scoped>
/* Agrega tus estilos aquí */
</style>
