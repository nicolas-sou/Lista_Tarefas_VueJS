<script setup>
    const props = defineProps (['tarefas']);
</script>

<template>
    <ul class="list-group mt-4">
        <li class="list-group-item my-2" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
    .done{
        text-decoration: line-through;
    }

    .list-group {
        margin-bottom: 24px;
    }

    .list-group-item{
        background-color: #ffffff;
    }
</style>