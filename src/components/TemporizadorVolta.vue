<template>
    <div class="is-flex is-align-itens-center is-justify-content-space-between">
                    <CronometroVolta :timeWithSeconds="timeWithSeconds"/>
                <button class="button" @click="iniciarVolta" :disabled="cronometroRodando">
                    <span class="icon">
                        <i class="fas fa-play"></i>
                    </span>
                    <span>play</span>
                </button>
                <button class="button" @click="finalizarVolta" :disabled="!cronometroRodando">
                    <span class="icon">
                        <i class="fas fa-stop"></i>
                    </span>
                    <span>stop</span>
                </button> 
            </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroVolta from './Cronometro.vue';
export default defineComponent({
    name:'TemporizadorVolta',
    emits:['voltaFinalizada'],
    components:{
        CronometroVolta
    },
    data () {
        return {
            timeWithSeconds:0,
            cronometro:0,
            tempoPausado:0,
            cronometroRodando:false,
        }
    },

    methods:{
        //inicia a contagem
        iniciarVolta () {
            this.cronometroRodando = true
            this.cronometro = setInterval(()=>{
                this.timeWithSeconds += 1
            },1000)
        },
        //Finaliza Volta
        finalizarVolta () {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('voltaFinalizada',this.timeWithSeconds)
            this.timeWithSeconds = 0
        },
    }
})
</script>
