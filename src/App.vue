<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
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
    Tarefa
  },
  methods: {
    salvarTarefa(tarefa: ITarefa): void {
      this.tarefas.push(tarefa);
      console.log(this.tarefas);
    }
  }
});
</script>


<style>
  .lista {
    padding: 1.25rem;
  }
</style>
