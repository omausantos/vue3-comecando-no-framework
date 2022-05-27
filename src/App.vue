<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <Box v-if="listaVazia">
          Nenhuma atividade cadastrada :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import Tarefa from './components/Tarefa.vue';
import ITarefa from './Interfaces/ITarefa';
import Box from './components/Box.vue';

export default defineComponent({
  name: 'App',
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  components: {
    BarraLateral,
    FormularioTarefa,
    Tarefa,
    Box
  },
  methods: {
    salvarTarefa(tarefa: ITarefa): void {
      this.tarefas.push(tarefa);
      console.log(this.tarefas);
    }
  },
  computed: {
    listaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  }
});
</script>


<style>
.lista {
  padding: 1.25rem;
}
</style>
