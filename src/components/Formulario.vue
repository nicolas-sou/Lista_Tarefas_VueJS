<script setup>
    const props = defineProps (['cadastraTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp'])
</script>

<template>
    <form @submit.prevent="props.cadastraTarefa">
        <div class="row">
            <div class="col">
                <input :value="props.tarefaTemp" @change="props.editaTarefaTemp" required
                    type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary" id="Cadastar">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.trocarFiltro" class="form-control">
                    <option value="Todas">Todas tarefas</option>
                    <option value="Pendentes">Pendentes</option>
                    <option value="Finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>

<style>
    #Cadastar{
        background-image: linear-gradient(249deg,#0d7ae0,#38c00b);
        border: none;
        color: #fff;
    }
    @media (max-width: 640px) {
        .form-control{
            margin-top: 20px;
        }

        #Cadastar{
            margin-top: 24px;
        }
    }
</style>