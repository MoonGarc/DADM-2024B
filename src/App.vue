<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');

// ---items----
const items = ref([
  { id: '0', label: '10 bolillos', purchased: false, priority: true },
  { id: '1', label: '1 chela', purchased: true, priority: true},
  { id: '2', label: 'leche', purchased: false, priority: false },
  { id: '3', label: '1 nutella', purchased: true, priority: true }
]);

// Item-Method
// Metodo para agregar nuevos elementos a la lista
const saveItem = () => {
  items.value.push({ 
    id: items.value.length + 1, 
    label: newItem.value,
    highPriority: newItemHighPriority.value
  });
  // Reiniciendo la entrada de texto
  newItem.value = "";
  newItemHighPriority.value = false;
};
// Funcion que alterna el valor de la variable editing
const doEdit = (edit) => {
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};

// --Formulario---
const newItem = ref("");
const newItemHighPriority = ref(false);
const editing = ref(true);
const activeEdition = (activate) => {
  editing.value = activate;
};// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};
</script>

<template>
  <div class="header">
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activeEdition(false)">
      Cancelar
    </button>
    <button v-else class="btn btn-primary" @click="activeEdition(true)">
      Agregar articulo
    </button>
  </div>

  <!-- Agrupando Entradas de usuario -->
  <form class="add-item form" v-if="editing" v-on:submit.prevent="saveItem">
    <!-- Entrada de texto -->
    <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
    <!-- Caja de seleccion de Prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta Prioridad
    </label>
    <!-- Boton -->
    <button 
    :disabled="newItem.length == 0"
    class="btn btn-primary">
      Salvar Articulo
    </button>
  </form>
    <!--LISTA OBJETOS-->
  <!-- Lista -->
  <ul>
    <li
      v-for="({ id, label, purchased, priority }, index) in items"
      @click="togglePurchased(items[index])"
      v-bind:key="id"
      :class="{ strikeout: purchased, priority: highPriority }"
    >
      ⚜ {{ label }}
    </li>
  </ul>
  <!--LISTA ARREGLOS-->
  <ul>
  <li 
  v-for="{ id, label, purchased } in items" 
  v-bind:key="id"
  :class="{strikeout: purchased}">🔹 {{ label }}</li>
</ul>
  <p v-if="items.length === 0"> 🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>