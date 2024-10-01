<script setup>
// Este código está utilizando Vue 3 <script setup>
// Más información en https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";

const header = ref("🛒 Shopping List App");
const items = ref([
  { id: 1, label: "10 bolillos" },
  { id: 2, label: "1 lata de frijoles" },
  { id: 3, label: "2 latas de atún" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);

// Función para agregar un nuevo artículo a la lista
const addItem = () => {
  if (newItem.value.trim() !== "") {
    const label = newItemHighPriority.value
      ? `⚡ ${newItem.value}` // Añadir un icono de alta prioridad si está marcado
      : newItem.value;
    items.value.push({
      id: items.value.length + 1,
      label: label,
    });
    newItem.value = ""; // Limpiar el campo de entrada
    newItemHighPriority.value = false; // Resetear la prioridad
  }
};
</script>

<template>
  <h1>{{ header }}</h1>
  
  <!-- Agrupando entradas de usuario -->
  <div class="add-item form">
    <!-- Entrada de texto -->
    <input 
      type="text" 
      placeholder="Add Item" 
      v-on:keyup.enter="addItem" 
      v-model.trim="newItem" />
    
    <!-- Caja de selección de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" /> Alta Prioridad
    </label>
    
    <!-- Botón -->
    <button 
      class="btn btn-primary" 
      v-on:click="addItem">
      Salvar Artículo
    </button>
  </div>

  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }) in items" :key="id">⚜ {{ label }}</li>
  </ul>
</template>
