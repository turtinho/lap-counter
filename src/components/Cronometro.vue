<template>
    <section>
        <strong class="display">
            {{tempoDecorrido}}
        </strong>
        </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name:'CronometroVolta',
    props: {
        timeWithSeconds: {
            type: Number,
            default:0
        }
    } ,
    computed: {
       tempoDecorrido ():string {
        return new Date(this.timeWithSeconds * 1000).toISOString().substring(14,19)
       }
    },
}) 
</script>

<style>
.display{
    color:var(--text-primary);
}
</style>