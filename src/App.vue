<template>
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <input type="text" placeholder="Add Item" v-model.trim="newItem">
    
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority">
      High Priority
    </label>
    
    <!-- Helados -->
    <label>
      <input type="checkbox" v-model="iceCreamFlavors" value="vanilla">
      Vanilla
    </label>
    <label>
      <input type="checkbox" v-model="iceCreamFlavors" value="chocolate">
      Chocolate
    </label>
    <label>
      <input type="checkbox" v-model="iceCreamFlavors" value="strawberry">
      Strawberry
    </label>
  
    {{ iceCreamFlavors }}
  
    <!-- Lista -->
    <ul>
      <li v-for="{ id, label } in items" v-bind:key="id">
        ⚜ {{ label }}
      </li>
    </ul>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const header = ref('App lista de compras');
  const items = ref([
    { id: '0', label: '10 bolillos' },  
    { id: '1', label: '1 lata frijoles' },
    { id: '2', label: '1 Chelas' },
    { id: '3', label: '1 nutella' },
  ]);
  const newItem = ref('');
  const newItemHighPriority = ref(false);
  const iceCreamFlavors = ref([]);
  </script>
  
  <style scoped>
  .shopping-cart-icon {
    font-size: 2rem;
  }
  </style>
  