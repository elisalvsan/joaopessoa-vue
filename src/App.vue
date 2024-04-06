<script setup>
import Home from '@/pages/Home.vue';
import AtracoesTuristicas from '@/pages/AtracoesTuristicas.vue';
import RoteiroViagem from '@/pages/RoteiroViagem.vue';

import { provide, ref } from 'vue';

const paginaSelecionada = ref(0)

const paginas = [
  { titulo: 'Home', componente: Home, path: '/' },
  { titulo: 'Atrações turísticas', componente: AtracoesTuristicas, path: '/atracoes' },
  { titulo: 'Roteiro de Viagem', componente: RoteiroViagem, path: '/roteiro' },
]

const roteiro = ref([])
provide('roteiro', roteiro)

</script>

<template>
  <header>
    <div class='menu'>
      <a v-for='(pagina, index) in paginas' :key='`pagina${index}`'
        @click='paginaSelecionada = index'>
        {{ pagina.titulo }}
        <span v-if="index === 2"> ({{ roteiro.length }})</span>
      </a>
    </div>
  </header>
  <main>
    <div>
      <KeepAlive>
        <component :is='paginas[paginaSelecionada].componente' />
      </KeepAlive>
    </div>
  </main>
</template>

<style scoped>
</style>
