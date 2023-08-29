<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  filtro: 'adição',
  firstNumber: 0,
  secondNumber: 0,
})

const getResultados = () => {
  const {filtro, firstNumber, secondNumber} = estado;

  switch(filtro) {
    case 'adição':
      return firstNumber + secondNumber;
    case 'subtração':
      return firstNumber - secondNumber;
    case 'multiplicação':
      return firstNumber * secondNumber;
    case 'divisão':
      return firstNumber / secondNumber;
  }
}
</script>

<template>
  <div class="container">
    <h1 class="mt-5 mb-4">Calculadora</h1>
    <form>
      <div class="row">
        <div class="col-md-5">
          <input required class="form-control mb-3" type="number" placeholder="Primeiro número" @keyup="evento => estado.firstNumber = parseInt(evento.target.value)">
        </div>
        <div class="col-md-5">
          <input required class="form-control mb-3" type="number" placeholder="Segundo número" @keyup="evento => estado.secondNumber = parseInt(evento.target.value)">
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="adição">Adição</option>
            <option value="subtração">Subtração</option>
            <option value="multiplicação">Multiplicação</option>
            <option value="divisão">Divisão</option>
          </select>
        </div>
      </div>
      <h4 class="bt-3">O resultado é {{ getResultados() }}</h4>
    </form>
  </div>
</template>

<style scoped>
</style>
