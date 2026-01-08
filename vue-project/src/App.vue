<script setup>
import {ref} from "vue";
let primeiroContador = ref(1);

let segundoContador = ref(1);

function aumentarContador(contador) {
    contador.value++;
}
function diminuirContador(contador) {
    contador.value--;
}
</script>

<template>
<div class="geral">
    <ul>
        <li>
            <div>{{primeiroContador.value}}</div>
            <button @click="aumentarContador(primeiroContador)">Aumentar</button>
            <button @click="diminuirContador(primeiroContador)">Diminuir</button>
        </li>
                <li>
            <div>{{segundoContador.value}}</div>
            <button @click="aumentarContador(segundoContador)">Aumentar</button>
            <button @click="diminuirContador(segundoContador)">Diminuir</button>
        </li>
    </ul>
</div>
</template>

<style scoped>
div {
    margin: auto;
}
</style>