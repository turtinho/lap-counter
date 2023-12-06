<template>
    <div class="box has.text.weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'BoxEstilo'
})
</script>

<style scoped>
.box{
    background-color: #C0C0C0;
    color:var(--text-primary)
}
</style>