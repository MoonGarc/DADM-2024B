<script setup>
import { ref } from 'vue';
//Modelo
const header = ref  ('App lista de compras');
const items = ref ([
{id: '0', label: '10 bolillos'},  
{id: '1', label:'1 lata frijoles'},
{id: '2', label: '1 Chelas'},
{id: '3', label: '1 nutella'},
]);
const newItem = ref('');
const newItemPriority = ref('low');
</script>

<template>
<h1> 
    <i class="material-icons shopping-cart-icon"> local_mall</i>
    {{ header }} 
    </h1>
    <input v-model.lazy="newItem" type="text" placeholder="Agregar Articulo">
    <!--Radio Buttons-->
    <label><input type="radio" value="low" v-model="newItemPriority">baja</label>
    <label><input type="radio" value="high" v-model="newItemPriority">alta</label>
    {{ newItemPriority == 'low' ? '🧊' : '🔥' }}    
    <ul>
        <li v-for= "({id, label}, i) in items" :key = "id">{{i+1}} {{ i%2==0?'🎇': '👜'}} {{ label }} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon {
font-size: 2rem;
}
</style>