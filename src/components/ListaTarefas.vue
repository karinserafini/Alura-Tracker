<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7">
               {{ task.description || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroTarefa :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </BoxComponent>
</template>
<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';
import BoxComponent from './BoxComponent.vue';

export default defineComponent ({
    name: "ListaTarefas",
    props:{
        task:{
            type: Object as PropType<ITarefa>, 
            required: true,
        }
    },
    components: {
    CronometroTarefa,
    BoxComponent,
},
})
</script>
