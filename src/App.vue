<template>
  <main class="columns is-gapless is-multiline" :class="{'darkMode': modoEscutoAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa 
          v-for="(tarefa, index) in tarefas" 
          :key="index" 
          :tarefa="tarefa"
        />

        <Box v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </Box>
      </div>    
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Box from './components/Box.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import ITarefa from './interface/ITarefa';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscutoAtivo: false
    }
  },
  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0;
    }
  },  
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    }, 
    trocarTema (modoEscuroAtivo: boolean) {
      this.modoEscutoAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25em
}
main {
  --bg-primary: #fff;
  --text-primary: #000;
  transition: all 0.3s ease;
}
main.darkMode {
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
  transition: all 0.3s ease;
}
.conteudo {
  background-color: var(--bg-primary);
}
</style>
