<script setup>
import { reactive, ref } from 'vue';

const estado = reactive({
  filter: 'resultado',
  num1: ref(0),
  num2: ref(0),
  operation: ref('+'),
  result: ref(0)
})

const operationAdicao = () => {
  return estado.num1 + estado.num2
}

const operationMenos = () => {
  return estado.num1 - estado.num2
}

const operationMultiplicacao = () => {
  return estado.num1 * estado.num2
}

const operationDivisao = () => {
  return estado.num1 / estado.num2
}

const calcular = () => {
  

  switch(estado.operation) {
    case '+':
        estado.result = operationAdicao();
      break;
    
      case '-':
       estado.result = operationMenos();
        break;

      case '*':
        estado.result = operationMultiplicacao()
        break;
    
    case '/':
      estado.result = operationDivisao()
      break;

    default:
      estado.result = 0;
  }
}
</script>

<template>
  <div class="calculadoraAritmetica">

    <form @submit.prevent="calcular">
      <div class="row">
        <div class="form-group col-sm-6">
          <div class="cabecalho">
            <h1>Calculadora Aritmética</h1>
          </div>
        <label for="num1" class="pt-4 pb-2 ">Digite o Número 1</label>
        <input type="number" class="form-control" @input="calcular" v-model="estado.num1">

        <select name="" id="" class="form-control mt-4" v-model="estado.operation">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>

        <label for="num1" class="pt-4 pb-2">Digite o Número 2</label>
        <input type="number" class="form-control" @input="calcular" v-model="estado.num2">

        <button type="submit" class="btn btn-primary mt-3" >Resultado</button>
        <textarea class="form-control mt-3" disabled cols="20" rows="5" >
          {{ estado.result.toFixed(2) }}
        </textarea>
      </div>
      
    </div>
  </form>

  </div>
</template>

<style scoped>
.row {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  margin: 25vh 0;
}

h1 {
  font-size: 2.5rem;
  font-family: sans-serif;
  font-weight: bold;
  letter-spacing: 2px;
  text-transform: uppercase;
  text-align: center;
}
</style>
