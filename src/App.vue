<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';
  import ListaDeTarefas from './components/ListaDeTarefas.vue';

  const estado = reactive( {
    filtro : 'todas',
    tarefaTemp: '',
    tarefas: []
})

const getTarefasPendentes = () => {
  return estado.tarefas.filter( tarefa => !tarefa.finalizada )
}
const getTarefasFinalizadas = () => {
  return estado.tarefas.filter( tarefa => tarefa.finalizada )
}

const getTarefasFiltradas = () => {
  const filtro = estado.filtro;

  switch ( filtro) {
    case 'pendentes':
      return getTarefasPendentes();
    case 'finalizadas':
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
}

const cadastrarTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false
  };
  estado.tarefas.push( tarefaNova );
  estado.tarefaTemp = '';
}
</script>

<template>
  <div class="container">
    <Cabecalho :getTarefasPendentes="getTarefasPendentes" />
    <Formulario :estado="estado" :cadastrarTarefa="cadastrarTarefa" />
    <ListaDeTarefas :getTarefasFiltradas="getTarefasFiltradas" />
  </div>
</template>


