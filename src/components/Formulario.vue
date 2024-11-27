<template>
    <form @submit.prevent="cadastraTarefa">
        <!-- '.prevent' = previne a ação padrão do submit, que é atualizar a pagina -->
        <div class="row">
            <div class="col">
                <input :value="estado.tarefaTemp" required @change="evento => estado.tarefaTemp = evento.target.value"
                    type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="evento => estado.filtro = evento.target.value" class="form-control">
                    <option value="todas">Todas as tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>