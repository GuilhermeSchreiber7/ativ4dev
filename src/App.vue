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
  if (novaCidade.value != "" && novaCidade.value != " ") {
    cidades.value.push(novaCidade.value)
    novaCidade.value = ''
  }
  }
  function remover(index) {
    cidades.value.splice(index, 1)
  }
  const OrdemAbc = computed(() => {
    return cidades.value.sort();
  });
  function Limpar(i){
    cidades.value.splice(i, cidades.value.length)
  }

  const showButton = computed(() => {
    return (novaCidade.value != "" && novaCidade.value != " ") ? true : false
  })
</script>

<template>
  <div class="addCity">
  <p>Adicionar Cidades</p>
  <input class="input" type="text" v-model="novaCidade" @keyup.enter="adicionar()">
  <button v-show="showButton" id="add" @click="adicionar">Adicionar</button>
  <button id="limpar" @click="Limpar(i)">Limpar</button>
  </div>
 <ul>
    <li v-for="(item, index) in OrdemAbc" :key="index"> {{ item }} <button @click="remover(index)">Remover</button> </li>
  </ul>
</template>

<style scoped>
 button {
    margin: 10px;
    padding: 10px;
    border: none;
    border-radius: 4px;
    background-color: #c92e2e;
    color: #fff;
    cursor: pointer;
  }
  #add{
    background-color:rgb(21, 119, 18)
  }
  button:hover {
    background-color: #882828;
  }
  .input{
    margin: 10px;
  }
  li{
    align-items: center;
    margin-bottom: 10px;
  }
#limpar{
  background-color: rgba(105, 105, 105, 0.637);
  color: black;
}


</style>
