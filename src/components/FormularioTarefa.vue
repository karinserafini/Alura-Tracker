<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <TemporizadorTarefa @timerEnded="endTask"/>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTarefa from './TemporizadorTarefa.vue'

export default defineComponent({
    name: 'FormularioTarefa',
    emits: ['WhenSavingTask'],
    components:{
      TemporizadorTarefa,
    },

    data() {
      return {
        taskDescription: ''
      }
    },

    methods: {
      endTask(elapsedTime: number) : void {
        this.$emit('WhenSavingTask', {
          durationInSeconds: elapsedTime,
          description: this.taskDescription
        })
        this.taskDescription = ''
      }
    }
})    
</script>
<style>
  .form {
    background-color: var(--bg-primary);
    color: var(--text-primary);
  }

</style>