<script setup>
import { reactive } from 'vue';

const estado = reactive ({
    numero01: 0,
    numero02: 0,
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

<select v-model="selected">
    <option disabled value="op">Por favor, selecione uma operação </option>
    <option> operacaoSoma</option>
    <option> operacaoSubtracao </option>
    <option> operacaoMultiplicacao </option>
    <option> operacaoDivisao</option>
</select>
<span>Selected: {{ operacaoSoma }}</span>

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

    <input type="number" @keyup="evento => estado.numero01 = evento.target.value" placeholder="Primeiro número">
    <br />
    <hr />

    <input type="number" @keyup="evento => estado.numero02 = evento.target.value" placeholder="Segundo número">

</template>

<style scoped>
</style>
