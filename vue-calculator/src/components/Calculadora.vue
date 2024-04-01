<template>
    <div class="container mt-5 border p-4 text-center">
      <h1 class="mb-4"><i class="bi bi-calculator me-2"></i>Calculadora Aritmética</h1>
      <div class="row justify-content-center">
        <div class="col-md-2">
          <input type="number" class="form-control" v-model="num1" @input="calcularResultado" placeholder="Primeiro número">
        </div>
        <div class="col-md-1">
          <select class="form-select" v-model="operacao" @change="calcularResultado">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>
        <div class="col-md-2">
          <input type="number" class="form-control" v-model="num2" @input="calcularResultado" placeholder="Segundo número">
        </div>
      </div>
      <div class="row mt-3">
        <div class="col-md-12">
          <h2 :class="{'text-black': num1 === '' && num2 === '', 'text-success': resultado > 0, 'text-danger': resultado < 0}">Resultado: {{ resultado }}</h2>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        num1: '',
        num2: '',
        operacao: '+',
        resultado: 0
      };
    },
    methods: {
      calcularResultado() {
        const num1 = parseFloat(this.num1);
        const num2 = parseFloat(this.num2);
  
        if (isNaN(num1) || isNaN(num2)) {
          this.resultado = 0;
          return;
        }
  
        switch (this.operacao) {
          case '+':
            this.resultado = num1 + num2;
            break;
          case '-':
            this.resultado = num1 - num2;
            break;
          case '*':
            this.resultado = num1 * num2;
            break;
          case '/':
            this.resultado = num2 !== 0 ? num1 / num2 : 'Indefinido';
            break;
          default:
            this.resultado = 0;
        }
      }
    }
  };
  </script>
  
  <style scoped>

  </style>