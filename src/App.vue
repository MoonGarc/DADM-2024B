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
</script>

<template>
  <h1>{{ header }}</h1>
  
  <!-- Agrupando en un div las entradas -->
  <form v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item form">
    <!-- Entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    
    <!-- Caja de selección de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    
    <!-- Botón -->
    <button class="btn btn-primary">
      Save Item
    </button>
  </form>

  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }) in items" :key="id">⚜ {{ label }}</li>
  </ul>
</template>
