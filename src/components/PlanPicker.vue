<script setup>
 import PlanPickerItem from './PlanPickerItem.vue';
 import {ref, onMounted} from 'vue';
 //Creando una referencia reactiva
 //para almacenar el plan seleccionado
 const selectedPlan = ref(null)
 const plans = 
 ref(['El cafetero','El chelero','El intelectual']);
 const selectPlan = (name) => {
  //Almacenar el plan seleccionado
selectedPlan.value = name;
   };
   // Intentando obtener la referencia al elemento .plans
   console.log("Termina de ejecutar el script setup 🥳");

   //registrando el hook mounted 
   onMounted(() =>{
    console.log("El componente planPicker se ha montado 🎉");
   });
</script>

<template>
<div class="plans">
  <PlanPickerItem
   v-for="plan in plans" 
   :key="plan"
    :name="plan"
    @select="selectPlan"
    :selected-plan="selectedPlan" />

</div>

</template>

<style scoped>

</style>
