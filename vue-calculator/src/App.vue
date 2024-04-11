<script setup>
  import { reactive } from 'vue'
  import Calculadora from './components/Calculadora.vue'

  const estado = reactive({
      operacao: 'adicao',
      sinalOperacao: '+',
      n1: 0,
      n2: 0,
      resultado: 0,
  })

  function getNumero(evento) {
      if (evento.target.id === 'n1') {
          estado.n1 = evento.target.value
      } else {
          estado.n2 = evento.target.value
      }
  }

  function getOperacao(evento) {
      estado.operacao = evento.target.value

      switch (estado.operacao) {
          case 'adicao':
              estado.sinalOperacao = '+'
              break;
          
          case 'subtracao':
              estado.sinalOperacao = '-'
              break;

          case 'multiplicacao':
              estado.sinalOperacao = 'x'
              break;

          case 'divisao':
              estado.sinalOperacao = '/'
              break;
      }
  }

  function calculaResultado() {
      if (estado.operacao === 'adicao') {
          return Number(estado.n1) + Number(estado.n2)
      } else if (estado.operacao === 'subtracao') {
          return Number(estado.n1) - Number(estado.n2)
      } else if (estado.operacao === 'multiplicacao') {
          return Number(estado.n1) * Number(estado.n2)
      } else if (estado.operacao === 'divisao') {
          return Number(estado.n1) / Number(estado.n2)
      }
  }
</script>

<template>
  <div class="container">
    <h1 class="title">Calculadora aritimética</h1>
    <Calculadora :n1="estado.n1" :n2="estado.n2" :operacao="estado.operacao" :sinalOperacao="estado.sinalOperacao" :recuperaOperacao="getOperacao" :recuperaNumero="getNumero" :resultado="calculaResultado()" />
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
