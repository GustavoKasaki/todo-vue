<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';
  import Lista from './components/Lista.vue';

  const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar SASS',
        finalizada: false,
      },
      {
        titulo: 'Ir para a academia',
        finalizada: true,
      }
    ]
    })

    const getTarefasPendentes = () => {
      return estado.tarefas.filter(tarefa => !tarefa.finalizada) // retorna as tarefas com atributo 'false'
    }

    const getTarefasFinalizadas = () => {
      return estado.tarefas.filter(tarefa => tarefa.finalizada) // retorna as tarefas com atributo 'false'
    }

    const getTarefasFiltradas = () => {
      // const filtro = estado.filtro; // recuperando o filtro (alternativo)
      const { filtro } = estado; // recuperando o filtro (desestruturação)

      switch (filtro) {
        case 'pendentes':
          return getTarefasPendentes();
        case 'finalizadas':
          return getTarefasFinalizadas();
        default:
          return estado.tarefas;
      }
    }

    const cadastraTarefa = () => {
      const tarefaNova = {
        titulo: estado.tarefaTemp,
        finalizada: false
      }
      estado.tarefas.push(tarefaNova);
      estado.tarefaTemp = '';
    }

    const possuiTarefasPendentes = () => {
      return getTarefasPendentes().length >= 1;
    }
    console.log(possuiTarefasPendentes());
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" :possui-tarefas-pendentes="possuiTarefasPendentes()"/>
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa" />
    <Lista :tarefas="getTarefasFiltradas()" />
  </div>
</template>