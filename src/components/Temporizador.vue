<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroForm :tempoEmSegundos="tempoEmSegundos"/>
    <BotaoNovo @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <BotaoNovo @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </section>
</template>

<script lang = "ts">

import { defineComponent } from "vue";
import CronometroForm from "./Cronometro.vue";
import BotaoNovo from "./Botao.vue";

export default defineComponent({
    name: "TemporizadorForm",
    emits:['aoTemporizadorFinalizado'],
    components: {
        BotaoNovo,
        CronometroForm
    },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando:false
        };
    },
    methods: {
        iniciar() {
            //começar a contagem
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    },
});

</script>