<template>
    <BoxEstilo>
        <div class="columns">
            <div class="column is-7">
                {{volta.descricao ||'There is no registered pilioto'}} 
            </div>
            <div class="column">
                <CronometroVolta :timeWithSeconds='volta.timeWithSeconds'/>
            </div>
        </div>
    </BoxEstilo>
</template>

<script lang="ts">
import Voltas from '@/interfaces/Voltas';
import { defineComponent , PropType} from 'vue';
import CronometroVolta from './Cronometro.vue';
import BoxEstilo from './boxEstilo.vue';
export default defineComponent({
    name:'VoltaQualy',
    components:{
        CronometroVolta,
        BoxEstilo
    },
    props:{
        volta:{
            type:Object as PropType<Voltas>,
                required: true,
        }
    },
})
</script>
