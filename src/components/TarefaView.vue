<template>
<BoxAlternativa>
<div class="column">
    <div class="columns is-7">
        {{tarefa.descricao || 'Tarefa Sem Descrição'}}
    </div>
    <div class="columun">
        <CronometroForm :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
    </div>
</div>
</BoxAlternativa>
</template>

<script lang="ts">

import Itarefa from "../Interfaces/ITarefa";
import { defineComponent, PropType } from "vue";
import CronometroForm from './Cronometro.vue';
import BoxAlternativa from './Box.vue';

export default defineComponent({
    name:'TarefaForm',
    components:{
        CronometroForm,
        BoxAlternativa
    },
    props:{
        tarefa:{
            type: Object as PropType<Itarefa>,
            required:true
        }
    }
})

</script>

