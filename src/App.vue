<script setup>
import { reactive } from 'vue';

const estado = reactive ({
    numero01: 0,
    numero02: 0,
    operacao: "+",
    resultado: 0,
})

const operacaoSoma = true
const operacaoSubtracao = false
const operacaoMultiplicacao = false
const operacaoDivisao = false

function mostrasoma() {
    const { numero01, numero02} = estado;
    return (numero01 + numero02);
}

function mostrasubtracao() {
    const { numero01, numero02} = estado;
    return numero01 - numero02
}

function mostramultiplicacao() {
    const { numero01, numero02} = estado;
    return numero01 * numero02
}

function mostradivisao() {
    const { numero01, numero02} = estado;
    return numero01 / numero02
}

</script>

<template>

<select v-model="operacao">
    <option disabled value="op">Por favor, selecione uma operação </option>
    <option> operação Soma</option>
    <option> operação Subtracao </option>
    <option> operação Multiplicacao </option>
    <option> operação Divisao</option>
</select>
<span>Selected: {{ operacaoSoma, operacaoSubtracao, operacaoMultiplicacao, operacaoDivisao }}</span>

    Número 01: {{ estado.numero01 }}
    Número 02: {{ estado.numero02 }}
    <br />
    <hr />

    <h1 v-if="operacaoSoma">Função Soma: {{ mostrasoma() }}</h1> 
    <h1 v-else-if="operacaoSubtracao">Função Subtração: {{ mostrasubtracao() }}</h1>
    <h1 v-else-if="operacaoMultiplicacao">Função Multiplicação: {{ mostramultiplicacao() }}</h1>
    <h1 v-else-if="operacaoDivisao">Função Divisão: {{ mostradivisao() }}</h1>
    <br />
    <hr />

    <input type="number" @keyup="evento => estado.numero01 = parseFloat(evento.target.value)" placeholder="Primeiro número">
    <br />
    <hr />

    <input type="number" @keyup="evento => estado.numero02 = parseFloat(evento.target.value)" placeholder="Segundo número">

</template>

<style scoped>
</style>