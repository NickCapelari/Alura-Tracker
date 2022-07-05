<template>
       <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <BoxAlternativa v-if="listaEstaVazia">
          Você não esta muito produtivo hoje
        </BoxAlternativa>
        <TarefaView v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
      </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormularioTarefa from '../components/Formulario.vue';
import TarefaView from '../components/TarefaView.vue';
import ITarefa from '../Interfaces/ITarefa'
import BoxAlternativa from '../components/Box.vue'
export default defineComponent({
  name: 'TarefasView',
  components: {
    FormularioTarefa,
    TarefaView,
    BoxAlternativa
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
    }
  },
  computed:{
    listaEstaVazia(): boolean{
      return this.tarefas.length===0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
  }
});
</script>
