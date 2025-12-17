<script setup>
    const nome = 'Pedro'
    const idade = 15

    function inverter(texto) {
        return texto.toLowerCase().split('').reverse().join('')
    }

    function saudacao() {
        return `Olá, ${nome}!`
    }
</script>

<template>
    <div class="info">
        <h1>Exemplo 1 - Mostrando informações na tela</h1>
        <p>Nome: {{ nome }} </p>
        <p>Idade: {{ idade }}  anos</p>
        <hr />
        <p>Para completar 50 anos faltam: {{ 50 - idade }}  anos</p>
        <p v-if="50-idade >= 10" class="novo">
          Está novo ainda!
        </p>
        <p v-if="50-idade < 10" class="velho">
          Está quase lá ein!
        </p>
        <p>O nome tem {{ nome.length }}  caracteres</p>
        <p>O nome invertido é: {{ inverter(nome) }} </p>
        <hr />
        <p> Exemplo de saudação usando função</p>
        <p> {{ saudacao() }}  </p>
    </div>
</template>

<style scoped>
.info {
  background-color: rgba(35,12,22,1);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
}

h1 {
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}
.novo {
  background-color: greenyellow;
  border-radius: 10px;
  font-size: 1rem;
  color: red;
  padding: 10px 15px;
}
.velho {
  background-color: red;
  border-radius: 10px;
  font-size: 1rem;
  padding: 10px 15px;
  color:greenyellow;
}
</style>