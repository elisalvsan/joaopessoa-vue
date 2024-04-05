<script setup>
import Home from '@/pages/Home.vue'

import { provide, ref } from 'vue';

const paginaSelecionada = ref(0)
const paginas = [{
  nome: 'Home',
  component: Home,
  path: '/'
}]

</script>

<template>
  <header>
    <div>
      <a v-for="(pagina, index) in paginas" :key="'pagina' + index" @click="paginaSelecionada = index">
        {{ pagina.nome }}
      </a>
    </div>
  </header>
  <div>
    <KeepAlive>
      <component :is='paginas[paginaSelecionada].component' />
    </KeepAlive>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
