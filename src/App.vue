<template>
  <main>
    <!--<pre></pre> visualiza como json-->
    <pre>{{ data }}</pre>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";

const data = ref([]);

const getData = async () => {
  const res = await fetch("https://hp-api.onrender.com/api/characters");
  //Cuando se ejecute el fetch quiero que los datos con los q responda la API se guarden en una constante llamada json
  const json = await res.json(); //para q lo formatee como jason y no lo pase como texto
  console.log(json);
  //cambio el id para hacerlo manejable
  const personajes = json.map((element, index) => {
    element.id = index + 1;
    return element;
  });
  console.log(personajes);
  data.value = personajes;
};
//console.log(getData()) //pending promise
onMounted(async () => {
  await getData();
});
</script>

<style scoped></style>
