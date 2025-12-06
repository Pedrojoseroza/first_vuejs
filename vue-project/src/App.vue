
<script setup>
import { ref, onMounted } from 'vue'

const contador = ref(0)

function incrementarContador() {
  contador.value++
}
function decrementarContador() {
  if (contador.value > 0) {
    contador.value--
  }
}
function resetaContador(){
  contador.value = 0;
}
onMounted(() => {
  console.log(`O valor inicial do contador é ${contador.value}.`)
})
</script>

<template>
  <p>Valor do contador é: {{ contador }}</p>
  <ul>
    <li>
      <button @click="resetaContador">Zera o contador</button>

    </li>
    <li>
      <button @click="decrementarContador">Decrementar</button>

    </li>
    <li>
      <button @click="incrementarContador">Incrementar</button>

    </li>
  </ul>
</template>

<style scoped>
button {
  font-weight: bold;
  background-color: aqua;
  color: red;
}
ul {
  display: flex;
  gap: 30px;
}
ul li {
  list-style: none;
}
</style>