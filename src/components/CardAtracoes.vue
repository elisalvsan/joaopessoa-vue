<script setup>
import { inject } from 'vue';

defineProps(['atracaoTuristica'])
const roteiro = inject('roteiro', [])
const emit = defineEmits(['enviarMensagem'])

const adicionaAtracaoAoRoteiro = (atracaoTuristica) => {
    if (roteiro.value.includes(atracaoTuristica)) {
        emit('enviarMensagem', 'Atração já adicionada ao seu roteiro de viagem.')
    } else {
        roteiro.value.push(atracaoTuristica)
    }
}
</script>
<template>
    <div>
        <section>
            <h2 class="nome-atracao"> {{ atracaoTuristica.nome }}</h2>
            <img class="imagem-atracao" :src="atracaoTuristica.imagem" :alt="atracaoTuristica.imagemDescricao">
            <p class='descricao-atracao'>{{ atracaoTuristica.descricao }}</p>
            <p class='footer-atracao'>{{ atracaoTuristica.endereco }}</p>
            <p class='footer-atracao'>{{ atracaoTuristica.visitacao }}</p>
            <button @click='() => adicionaAtracaoAoRoteiro(atracaoTuristica)'>Adicionar ao roteiro</button>
        </section>
    </div>
</template>

<style scoped>
div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
}

section {
    margin: 10px;
    padding: 10px;
    border: 1px solid lightgray;
    border-radius: 10px;
    box-shadow: 2px 2px 2px lightgray;

}

.nome-atracao {
    text-align: center;
    font-size: 20px;
    font-weight: 700;
}

.imagem-atracao {
    width: 100%;
    height: 100%;
}

.descricao-atracao {
    font-size: 1.125rem;
    text-indent: 2rem;
    text-align: justify;
    margin: 10px;
}

.footer-atracao {
    text-align: right;
    margin: 0 auto;
}

button {
    width: 100%;
    margin-top: 20px;
    padding: 10px 50px;
    background-color: #57b7d9;
    border: none;
    border-radius: 10px;
    color: #000;
    font-size: .875rem;
    cursor: pointer;
}
</style>