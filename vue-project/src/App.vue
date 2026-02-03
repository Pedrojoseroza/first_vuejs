<script setup>
  import { ref } from 'vue';
  import ProductList from './components/productList.vue';

  const produtos = ref([
    { id: 1, nome: 'Produto 1', preco: 19.99 },
    { id: 2, nome: 'Produto 2', preco: 29.99 },
    { id: 3, nome: 'Produto 3', preco: 39.99 },
  ]);

  function removerItem(id) {
    const index = produtos.value.findIndex((produto) => produto.id === id);
    produtos.value.splice(index, 1);
  }
</script>

<template>
  <product-list :produtos="produtos" @remove="removerItem" />
</template>
