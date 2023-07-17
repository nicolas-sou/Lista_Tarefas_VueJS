<script setup>
    const props = defineProps (['tarefasPendentes'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas Tarefas</h1>
        <p>
            Você possui {{ props.tarefasPendentes }} tarefas pendentes
        </p>
    </header>
</template>

<style>
    .bg-light {
    background-image: linear-gradient(5deg,#0d7ae0,#38c00b)!important;
    color: #fff;
}
</style>