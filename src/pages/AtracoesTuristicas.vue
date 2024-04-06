<script setup>
import {ref, watch} from 'vue';
import CardAtracoes from '@/components/CardAtracoes.vue';

let atracoesTuristicas = ref([])

fetch('/atracoes.json')
    .then(resposta => resposta.json())
    .then(dados => atracoesTuristicas.value = dados)

const mensagem = ref(null)
watch(mensagem, (novaMensagem) => {
  if (novaMensagem) {
    setTimeout(() => mensagem.value = null, 4000)
  }
})

function enviarMensagem(novaMensagem) {
  mensagem.value = novaMensagem
}

</script>
<template>
  <h1 class="titulo">Atrações turísticas</h1>
  <p class="total-atracoes">Total de atrações: {{ atracoesTuristicas.length }}</p>
  <div class="alert alert-danger" role="alert" v-if='mensagem'>{{ mensagem }}</div>
  <CardAtracoes class="card-atracoes"
      v-for='(atracaoTuristica, indice) in atracoesTuristicas'
      @enviar-mensagem='enviarMensagem'
      :key='`atracaoTuristica${indice}`'
      :atracaoTuristica='atracaoTuristica'/>
</template>

<style scoped>

.titulo{
  text-align: center;
  margin-top: 20px;
  text-transform: uppercase;
  font-weight: 700;
  color: #000;
}

.total-atracoes{
  text-align: center;
  text-transform: uppercase;
}

.alert{
  margin-top: 20px;
  margin-bottom: 20px;
  text-align: center;
  text-transform: uppercase;
  font-weight: 700;
  color: #000;
  background-color: rgba(50, 121, 179, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  padding: 10px;
  width: 100%;
}

.card-atracoes{
  width: 80%;
  margin-top: 20px;
  margin-left: auto;
  margin-right: auto;
  
}

</style>
