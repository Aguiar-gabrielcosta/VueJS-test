<script setup>
    import { reactive } from 'vue'

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
    <select @change="getOperacao" class="seletor">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
    </select>
    <form>
        <div class="campo">
            <label for="n1">Número 1:</label>
            <input @change="getNumero" @keyup="getNumero" id="n1" class="campo--entrada" type="number" value="0" step="1" required>
        </div>
        <span class="sinal">{{ estado.sinalOperacao }}</span>
        <div class="campo">
            <label for="n2">Número 2:</label>
            <input @change="getNumero" @keyup="getNumero" id="n2" class="campo--entrada" type="number" value="0" step="1" required>
        </div>
        <span>=</span>
        <span class="resultado">{{ calculaResultado() }}</span>
    </form>
</template>

<style scoped>
    .seletor {
        margin: 32px 0;
        font-size: 18px;
        padding: 3px;
        text-align: center;
    }

    form {
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        justify-content: space-evenly;
        font-size: 18px;
        font-weight: bold;
        column-gap: 18px;
        row-gap: 8px;
    }

    .campo {
        display: flex;
        align-items: center;
    }

    .campo > input {
        width: 50px;
        margin-left: 6px;
        font-size: 16px;
    }

    .resultado {
        border: 1px solid black;
        padding: 4px;
        width: 220px;
        text-align: end;
    }
</style>