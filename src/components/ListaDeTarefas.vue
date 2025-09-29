<script setup>
    const props = defineProps( ['getTarefasFiltradas'] )
</script>

<template>
    <div>
        <ul v-if="getTarefasFiltradas().length > 0" class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in getTarefasFiltradas()">
                <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                    :id="tarefa.titulo" type="checkbox">
                <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">{{ tarefa.titulo }}</label>
            </li>
        </ul>
        <div v-else class="mt-4 text-center text-muted">Não há tarefas.</div>
    </div>
</template>

<style scoped>

.done {
    text-decoration: line-through;
}

</style>