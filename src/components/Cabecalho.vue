<script setup>
    const props = defineProps( ['getTarefasPendentes'] );
</script>

<template>
    <header class="p-5 mb-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui {{ getTarefasPendentes().length }} tarefas pendentes
        </p>
    </header>
</template>