<script setup>
import { ref } from 'vue';

let jp = ref({})

fetch('/sobreJP.json')
    .then(res => res.json())
    .then(data => jp.value = data)

</script>

<template>
    <div v-for="(jp, index) in jp" :key="'item' + index">
        <h1 class="titulo">{{ jp.nome }}</h1>
        <img class="imagem-postal" :src="jp.imagem" alt="imagem de João Pessoa - Paraiba ">
        <div class="sobre">
            <h2 class="topico">Um pouco de sua historia</h2>
            <p class="texto">{{ jp.historia }}</p>
            <h2 class="topico">Atrativos</h2>
            <p class="texto">{{ jp.atrativos }}</p>
        </div>
    </div>
</template>

<style scoped>

.titulo{
    text-transform: uppercase;
    font-size: 30px;
    font-weight: 700;
    color: #000000;
    margin-top: 20px;
    margin-bottom: 20px;
}

.imagem-postal{
    width: 100%;
}

.topico{
    text-transform: uppercase;
    font-size: 18px;
    font-weight: 700;
    color: #000000;
    margin-top: 5px;
    margin-bottom: 10px;
}

.texto{
    font-size: 18px;
    font-weight: 400;
    color: #000000;
    margin-top: 5px;
    margin-bottom: 10px;
}

p{
    text-align: justify;
    font-size: 18px;
    word-break: break-word;
}

.sobre{
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;

}

</style>