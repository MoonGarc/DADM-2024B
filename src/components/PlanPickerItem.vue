<template>
  <div @click="selectedPlan"
   class="plan"
   :class="{ selected: isSelected}">
    <div class="description">
      <span class="title">
         {{ name }} {{ isSelected ? '🌟' : '' }}  </span>
    </div>
  </div>
</template>

<script setup>
//Importamos la funcion para crear
//propiedades computada 
import { computed } from 'vue';
// Usando macro para definir las props
// definir las props
//define props (['name', 'planIcon']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }, 
  selectedPlan: String
  
 });
//Define event 
const emit = defineEmits(['select']); 
//Función que permite cambiar el estado de la variable
// selected
const selectedPlan = () => {
   //Emitir que el evento ha sido seleccionado
  //plan ha sido seleccionado
emit('select', props.name);
};
//Creando una propiedad computada 
//para saber si el plan ha sido seleccionado
const isSelected = computed (() =>{
  return props.name === props.selectedPlan;
});
</script>

<style scoped>
/* Agrega tus estilos aquí */
</style>