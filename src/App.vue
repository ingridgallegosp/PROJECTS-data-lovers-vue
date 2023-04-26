<template>
    <main>
        <!--<pre> visualiza como json-->
        <!-- <pre>{{ data }}</pre> -->
        <Card 
            v-for="personajes in data" 
            :key="personajes.id" 
            :image="personajes.image"
            :id="personajes.id" 
            :name="personajes.name"
            :actor="personajes.actor"
            :house="personajes.house"
        />
    </main>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Card from "./components/Card.vue";

const data = ref([]);

const getData = async () => {
    const res = await fetch("https://hp-api.onrender.com/api/characters");

    //Cuando se ejecute el fetch quiero que los datos con los q responda la API se guarden en una constante llamada json
    const json = await res.json(); //para q lo formatee como json y no lo pase como texto
    console.log(json);

    //se mapea el id para hacerlo manejable
    const personajes = json.map((element, index) => {
        element.id = index + 1;
        return element;
    });
    //console.log(personajes);

    //Cambia el estado de data con el valor actual de id mapeado
    data.value = personajes;
};
//console.log(getData()) //pending promise

onMounted(async () => {
    //resuleve la promesa pendiente
    await getData();
});
</script>

<style scoped>

</style>
