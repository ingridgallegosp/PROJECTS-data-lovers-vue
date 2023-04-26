<template>
    <div class="card">
        <img :src="image" :alt="name"/> <!-- : para pasar como atributo -->
        <span class="id">{{ id }}</span> -<!-- {{  }} para pasar como variable -->
        <h3 class="name">{{ name }}</h3> 
        <span class="actor">{{ actor }}</span> 
        <span class="house">{{ house }}</span>
    </div>
</template>

<script setup>
const props = defineProps(['id', 'name', 'actor', 'image', 'house']);

</script> 

<style scoped>
.card{
    width: 25%;
    height: 25%;
} 
</style>