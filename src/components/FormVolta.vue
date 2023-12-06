<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para a criação e voltas rápidas ">
                <input type="text"
                       class="input"
                       placeholder="Which pilot to insert?"
                       v-model="descricaoVolta"/>
            </div>
            <div class="column">
                <TemporizadorVolta @volta-finalizada="pararVolta"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorVolta from './TemporizadorVolta.vue';
export default defineComponent({
    name:'FormVolta',
    emits:['aoSalvarVolta'],
    components:{
        TemporizadorVolta
    },
    data(){
        return {
            descricaoVolta:''
        }
    },
    methods:{
        pararVolta(tempoDecorrido:number):void{
            this.$emit('aoSalvarVolta',{
                timeWithSeconds:tempoDecorrido,
                descricao:this.descricaoVolta
            })
            this.descricaoVolta = ''
        }
    }
})
</script>

<style>
.formulario{
    color: var(--text-primary);
    background-color: var(--bg-primary);
}
</style>




