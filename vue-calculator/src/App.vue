<script setup>
  import Calculadora from './components/Calculadora.vue'
</script>

<template>
  <div class="container">
    <h1 class="title">Calculadora aritimética</h1>
    <Calculadora />
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: white;
    max-width: 650px;
    width: 100%;
    padding: 64px;
    border-radius: 10px;
  }

  .title {
    text-align: center;
  }
</style>

<style>
  body {
    background-color: rgb(77, 162, 162);
    min-height: 100vh;
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
  }

  #app {
    width: 100%;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
