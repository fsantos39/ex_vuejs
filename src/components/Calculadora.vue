<script setup>
    import { reactive } from 'vue';

    const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacoes: {
    soma: (a, b) => a + b,
    subtracao: (a, b) => a - b,
    multiplicacao: (a, b) => a * b,
    divisao: (a, b) => (b !== 0 ? a / b : 'Divisao por zero'),
    },
    resultado: 0,
});

const calculaResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    const num1 = parseFloat(primeiroNumero);
    const num2 = parseFloat(segundoNumero);
    estado.resultado = !isNaN(num1) && !isNaN(num2) ? estado.operacoes[operacaoMatematica](num1, num2) : 'Entrada inválida';
};
</script>

<template>
    <div class="container">
        <div class="calculadora">
            <h1 class="mt-5 mb-3">Calculadora Aritmética</h1>
            <input class="form-control" type="text" v-model="estado.primeiroNumero" @input="calculaResultado" />
            <select class="mt-3 mb-1" v-model="estado.operacaoMatematica" @change="calculaResultado">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
            </select>
            <input type="text" class="form-control mt-2" v-model="estado.segundoNumero" @input="calculaResultado" /> <br />
            <p>
                Resultado: {{ estado.resultado }}
            </p>
        </div>
    </div>
</template>

<style>
    .container{
        font-family: Arial, sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 25vh;
        border-radius: 10px;
    }
    .calculadora {
        background: #96989C;
        border-radius: 10px;
        margin: 10px 0;
        padding: 10px;
        width: 50%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        
    }


</style>