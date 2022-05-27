<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao" />
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizar"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Temporizador from './Temporizador.vue';

export default defineComponent({
    name: 'FormularioTarefa',
    data () {
        return {
            descricao: '',
        }
    },
    components: {
        Temporizador
    },
    methods: {
        finalizar(tempoEmSegundos: number): void {
            console.log('tempoEmSegundos', tempoEmSegundos);
            console.log('descricao', this.descricao)
        }
    }
})
</script>
