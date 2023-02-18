<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
          <CronometroTarefa :timeInSeconds="timeInSeconds"/>
          <BotaoCronometro @clicked="startTask" icon="fas fa-play" text="play" :disabled="timerRunning"/>
          <BotaoCronometro @clicked="endTask" icon="fas fa-stop" text="stop" :disabled="!timerRunning"/>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue'
import BotaoCronometro from './BotaoCronometro.vue';

export default defineComponent({
    name: 'TemporizadorTarefa',
    emits: ['timerEnded'],
    components: {
     CronometroTarefa,
     BotaoCronometro,
    },

    data() {
      return {
        timeInSeconds: 0,
        timer: 0,
        timerRunning: false,
      }
    },
    
    methods: {
      startTask(){
        this.timerRunning = true
        this.timer = setInterval(() => {
          //método para iniciar a contagem do temporizador
          this.timeInSeconds += 1
        }, 1000)
      },

      endTask() {
        this.timerRunning = false
        clearInterval(this.timer)
        this.$emit('timerEnded', this.timeInSeconds)
        this.timeInSeconds = 0
      }
    }

})
</script>