<template>
    <button 
      @mouseenter="hover = true"
      @mouseleave="hover = false"> 
      <slot name="icon">➡️</slot>
      <slot>Submit</slot>
    </button>
    {{ hover }}
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const hover = ref(false);
  </script>