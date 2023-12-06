<template>
  <main class="columns is-gapless is-multine" :class="{'dark-mode':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <LateralBar @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter content">
      <FormVolta @aoSalvarVolta="salvarVolta"/>
      <div class="list">
        <ListaVoltas v-for="(volta, index) in ordenarPorMenorTempo(voltas)" :key="index" :volta="volta"/>
        <BoxEstilo v-if="listaVazia">
          There are no laps recorded 
      </BoxEstilo>
      </div>
      
</div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import LateralBar from './components/LateralBar.vue';
import FormVolta from './components/FormVolta.vue';
import ListaVoltas from './components/ListaVoltas.vue';
import Voltas from './interfaces/Voltas';
import BoxEstilo from './components/boxEstilo.vue'

export default defineComponent({
  name: 'App',
  components:{
    LateralBar,
    FormVolta,
    ListaVoltas,
    BoxEstilo
  },
  data(){
    return{
      voltas:[] as Voltas[],
      modoEscuroAtivo:false
    }
  },
  methods: {
    salvarVolta(volta:Voltas){
      this.voltas.push(volta)
    },
    trocarTema(modoEscuroAtivo: boolean){
    this.modoEscuroAtivo = modoEscuroAtivo
  },
  ordenarPorMenorTempo(lista: Voltas[]): Voltas[] {
      return lista.slice().sort((a, b) => a.timeWithSeconds - b.timeWithSeconds);
        },
  },
  computed:{
    listaVazia() :boolean {
      return this.voltas.length === 0
    }
  }
});
</script>

<style>
.list{
  padding: 1.25rem;
}
main{
  --bg-primary:#FFFFFF;
  --text-primary:#000000;
}
main.dark-mode{
  --bg-primary:#4F4F4F;
  --text-primary:#FFFFFF;
}
.content{
  background-color: var(--bg-primary);
}
</style>