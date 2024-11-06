<template>
  <div class="plan">
    <div class="description">
      <span class="title">
         {{ name }} 
      </span>
    </div>
  </div>
</template>

<script setup>
// Usando macro para definir las props
defineProps({
  name: {
    type: String,
    required: true
  },
 
});
</script>

<style scoped>
/* Agrega tus estilos aquí */
</style>
