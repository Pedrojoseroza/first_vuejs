<script setup>
  import { computed, ref } from 'vue';

  const showContent = ref(false);
  const buttonText = computed(() =>
    showContent.value ? 'Esconder' : 'Mostrar',
  );
</script>

<template>
  
  <button @click="showContent=!showContent">{{buttonText}}</button>
  <div v-if="showContent" class="expand-box">
    Conteúdo da caixa de expansão.
  </div>
  
</template>

<style scoped>
  .expand-box {
    height: 100%;
    padding: 20px;
    border: 1px solid gray;
    border-radius: 5px;
    box-shadow: 3px 3px 2px 2px gray;
  }
</style>