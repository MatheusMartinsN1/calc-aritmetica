<script setup>
import { reactive, computed } from 'vue';

const estado = reactive ({
    num1: 0,
    num2: 0,
    operacoes: 'soma', 
})

const simboloOperacao = computed(() => {
    switch (estado.operacoes) {
        case 'soma': return '+'
        case 'subtracao': return '-'
        case 'multiplicacao': return '*'
        case 'divisao': return '/'
    }
})

const resultado = computed(() => {
    switch (estado.operacoes) {
        case 'soma': return estado.num1 + estado.num2;
        case 'subtracao': return estado.num1 - estado.num2;
        case 'multiplicacao': return estado.num1 * estado.num2;
        case 'divisao': return estado.num2 !== 0 ? (estado.num1 / estado.num2) : 'Erro: Divisão por zero'
    }
})

</script>

<template>
    <form action="" @submit.prevent>
        
        <input v-model.number="estado.num1"  type="number">

        <span class="p-3"> {{ simboloOperacao }} </span>

        <input v-model.number="estado.num2" type="number">

        <select v-model="estado.operacoes" class="form-select-sm ms-2" name="" id="">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select>
    </form>

    <h2 >Resultado: {{ resultado }}</h2>
</template>
