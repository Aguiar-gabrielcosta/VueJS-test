<script setup>
    const props = defineProps(['n1', 'n2', 'operacao', 'sinalOperacao', 'recuperaOperacao', 'recuperaNumero', 'resultado']);
</script>

<template>
    <select @change="props.recuperaOperacao" class="seletor">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
    </select>
    <form>
        <div class="campo">
            <label for="n1">Número 1:</label>
            <input @change="props.recuperaNumero" @keyup="props.recuperaNumero" id="n1" class="campo--entrada" type="number" value="0" step="1" required>
        </div>
        <span class="sinal">{{ props.sinalOperacao }}</span>
        <div class="campo">
            <label for="n2">Número 2:</label>
            <input @change="props.recuperaNumero" @keyup="props.recuperaNumero" id="n2" class="campo--entrada" type="number" value="0" step="1" required>
        </div>
        <span>=</span>
        <span class="resultado">{{ props.resultado }}</span>
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