<script setup>
    const props = defineProps(['tarefasPendentes', 'possuiTarefasPendentes']);
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <p v-if="props.possuiTarefasPendentes">Você possui {{ props.tarefasPendentes }} tarefas pendentes!</p>
        <p v-else>Você não possui tarefas pendentes, vá ler um livro!</p>
    </header>
</template>