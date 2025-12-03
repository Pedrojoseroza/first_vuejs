
<script>
export default {
  data() {
    return {
      contador: 0
    }
  },
  methods: {
    incrementarContador() {
      this.contador++
    },
    decrementarContador() {
      if (this.contador > 0) {
        this.contador--
      }
    },
    resetaContador() {
      this.contador = 0;
    }
  },
  mounted() {
    console.log(`O valor inicial do contador é ${this.contador}.`)
  }
} // Será apresentado a seguir
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