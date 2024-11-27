<script setup>
    const props = defineProps(['tarefasPendentes']);
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <p v-if="isVisible">
            Você possui {{ props.tarefasPendentes }} tarefas pendentes!
        </p>
    </header>
</template>