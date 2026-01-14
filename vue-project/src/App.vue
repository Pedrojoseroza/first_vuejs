<script setup>
  import { ref } from 'vue';
  const cidades = ref([
  'São Paulo',
  'Rio de Janeiro',
  'Belo Horizonte',
  'Salvador',
  'Fortaleza',
  'Curitiba',
  'Manaus',
  'Recife',
  'Porto Alegre',
  'Brasília',
].sort());
let novaCidade = ref(' ');
function adicionarCidade() {
  if (novaCidade.value !== null || novaCidade.value.trim() !== " ") {
    cidades.value.push(novaCidade.value.trim());
    cidades.value.sort()
    novaCidade.value = " ";
  
    
  } else {
    alert("Informe uma cidade válida");
  }
}

</script>

<template>
<h1>
  Lista de Cidades
</h1>
<p>
  Adicione sua cidade abaixo: 
</p>
<input type="text" v-model="novaCidade">
<input type="button" @click="adicionarCidade" value="Adicionar">
<ul>
  <li v-for="cidade in cidades">
    {{ cidade }}
  </li>
</ul>
</template>

<style scoped>
ul li {
  color: red;
}
</style>