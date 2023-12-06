<template>
    <header>
        <h1>
            <img src="../assets/formula-1-logo-0.png" alt="">
        </h1>
        <h2>
            Welcome to the First Page of Forumla 1, using vue.js
        </h2>
        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name:"LateralBar",
    emits:['aoTemaAlterado'],
    data (){
        return{
            modoEscuroAtivo: false
        }
    },
    computed:{
        textoBotao(){
            if(this.modoEscuroAtivo){
                return "Disable Dark Mode"
            }
            return "Enable Dark Mode"
        }
    },
    methods:{
        alterarTema(){
        this.modoEscuroAtivo = !this.modoEscuroAtivo
        this.$emit('aoTemaAlterado',this.modoEscuroAtivo)
        }
    }
})
</script>

<style scoped>
header {
    padding: 1rem;
    background:#000000 ;
    width: 100%;
    height: 100vh;
    text-align: center;
    color: #ffffff;
    background-color: #000000;
}
@media only screen and (max-width: 768px){
    header{
        padding:2.5rem;
        height:auto;
    }
}
.button{
    color: #ffffff;
    background-color: #000000;
    margin-top: 210px;
}
</style>
