<script setup>
  import { reactive, computed } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';
  import ListaDeTarefas from './components/ListaDeTarefas.vue';

  const estado = reactive({
    filtro: 'Todas',
    tarefaTemp: '',
    tarefas: []
  });

  const exibirAviso = computed(() => {
    return getTarefasPendentes().length === 0 && estado.filtro === 'Pendentes';
  });

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  const getTarefasFiltradas = () => {
    const { filtro } = estado;

    switch (filtro) {
      case 'Pendentes':
        return getTarefasPendentes();
      case 'Finalizadas':
        return getTarefasFinalizadas();
      default:
        return estado.tarefas;
    }
  }

  const cadastraTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizada: false,
    };
    estado.tarefas.push(tarefaNova);
    estado.tarefaTemp = '';
  };
</script>

<template>
  <div class="container" style="padding-bottom: 40px;">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp= evento.target.value" :cadastra-tarefa="cadastraTarefa"/>
    <div v-if="exibirAviso" class="aviso rounded-2">Não há tarefas pendentes.</div>
    <ListaDeTarefas :tarefas="getTarefasFiltradas()" :marcar-concluida="marcarComoConcluida"/>
  </div>
</template>

<style>
  #fundo{
    background-image: linear-gradient(91deg,#65a0d4,#6bc783);
  }

  .aviso {
    margin-top: 24px;
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    color: #fff;
    border: 24px;
  }
</style>