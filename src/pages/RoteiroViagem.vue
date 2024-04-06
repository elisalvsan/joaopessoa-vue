<script setup>
import { inject } from 'vue';

const roteiro = inject('roteiro')

const excluirAtracao = (atracaoTuristica) => {
    const indice = roteiro.value.indexOf(atracaoTuristica)
    roteiro.value.splice(indice, 1)
}

</script>

<template>
    <section>
        <h1 class="titulo">Roteiro de Viagem</h1>
        <table>
            <thead>
                <tr>
                    <th>Ordem da visita</th>
                    <th>Nome da atração</th>
                    <th>Endereço</th>
                    <th>Visitação</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(atracaoRoteiro, index) in roteiro" :key="`atracaoRoteiro${index}`">
                    <td>{{ index + 1 }}</td>
                    <td>{{ atracaoRoteiro.nome }}</td>
                    <td>{{ atracaoRoteiro.endereco }}</td>
                    <td>{{ atracaoRoteiro.visitacao }}</td>
                    <td>
                        <button @click="excluirAtracao(atracaoRoteiro)">Excluir</button>
                    </td>
                </tr>
            </tbody>
            <tfoot>
                <td colspan="5" class="total-selecionada">
                    Total de atrações: {{ roteiro.length }}
                </td>
            </tfoot>
        </table>
    </section>
</template>

<style scoped>

section{
    top: 0;
    left: 0;
    width: 80vw;
    height: 100vh;
}

.titulo {
    text-align: center;
    text-transform: uppercase;
    font-size: 30px;
    font-weight: 700;
    color: #000000;
    margin-top: 20px;
    margin-bottom: 20px;
}

table {
    width: 100%;
    border-collapse: collapse;
    border: 2px solid rgba(50, 121, 179, 0.8);
    margin-bottom: 20px;
    border-radius: 10px;
    word-break: break-word;
}

table>thead>tr>th {
    border: 2px solid rgba(50, 121, 179, 0.8);
    padding: 10px;
    text-align: center;
    font-weight: 700;
    color: #000000;

}

table>tbody>tr>td {
    border: 2px solid rgba(50, 121, 179, 0.8);
    padding: 10px;
    text-align: center;
    font-weight: 500;
    color: #000000;
}

.total-selecionada {
    text-align: left;
    font-weight: 500;
    color: #000000;
    margin-top: 20px;
    margin-bottom: 20px;

}

button {
    width: auto;
    height: auto;
    background-color: rgba(50, 121, 179, 0.8);
    border: none;
    border-radius: 10px;
    padding: 10px 20px;
    color: #fff;
    cursor: pointer;
    word-break: normal;
    font-size: 16px;
}
</style>