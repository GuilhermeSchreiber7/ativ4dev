<script setup>
import { ref, computed } from 'vue';
const cidades = ref([
  'São Paulo',
  'Rio de Janeiro',
  'Belo Horizonte',
  'Salvador',
  'Fortaleza',
  'Curitiba',
  'Manaus',
  'Recife',
  'Porto Alegre',
  'Brasília',
]);
const novaCidade = ref(``);

function adicionar() {
    cidades.value.push(novaCidade.value)
    novaCidade.value = ''
  }
  function remover(index) {
    cidades.value.splice(index, 1)
  }
  const OrdemAbc = computed(() => {
    return cidades.value.sort();
  });
</script>

<template>
  <input type="text" v-model="novaCidade">
  <button @click="adicionar">Adicionar</button>
 <ul>
    <li v-for="(item, index) in OrdemAbc" :key="index"> {{ item }} <button @click="remover(index)">Remover</button> </li>
  </ul>
</template>

<style scoped>

</style>
