<script setup>
import {ref, computed} from "vue";
let primeiroContador = ref(1);

let segundoContador = ref(1);

function aumentarPrimeiroContador() {
    primeiroContador.value++;
}
function diminuirPrimeiroContador() {
    primeiroContador.value--;
}
function aumentarsegundoContador() {
    segundoContador.value++;
}
function diminuirsegundoContador() {
    segundoContador.value--;
}
const soma = computed(() => primeiroContador.value + segundoContador.value)
const maiorque10 = computed(() => primeiroContador.value + segundoContador.value >= 10)
const menorque10 = computed(() => primeiroContador.value + segundoContador.value < 10)

</script>

<template>
<div class="geral">
    <ul>
        <li>
            <div>{{primeiroContador}}</div>
            <button @click="aumentarPrimeiroContador()">Aumentar</button>
            <button @click="diminuirPrimeiroContador()">Diminuir</button>
        </li>
        
        <li>
            <div>{{segundoContador}}</div>
            <button @click="aumentarsegundoContador()">Aumentar</button>
            <button @click="diminuirsegundoContador()">Diminuir</button>
        </li>
    </ul>
    <div class="soma">
        <p>
            A soma dos contadores ao lado é {{ soma }}
        </p>
    </div>
    <div class="par" v-if="soma % 2 == 0">
        A SOMA DOS CONTADORES É PAR
    </div>
    <div class="impar" v-else>
        A SOMA DOS CONTADORES É ÍMPAR
    </div>
    <div v-show="maiorque10" class="mais10">
        A SOMA É MAIOR QUE 10!!!
    </div>
    
    <div v-show="menorque10" class="mais10">
        A SOMA É MENOR QUE 10!!!
    </div>
</div>
</template>

<style scoped>
    div.geral {
        display: flex;
        padding: 35px 0;
    }
    div.soma {
        margin: 0 30px;
    }
    div.soma p {
        font-size: larger;
    }
    div.par {
        background-color: red;
        color: white;
        padding: 30px;
    }
    div.impar {
        background-color: blue;
        color: white;
        padding: 30px;
    }
    div.mais10 {
        margin: 0 0 0 30px;
        padding: 30px;
        background-color: greenyellow;
        color: white;
    }
    li {
        list-style-type: none;        
    }
 li div {
    margin: auto 0 auto 50px;

}
 li button {
    margin: 8px 5px;
}
</style>