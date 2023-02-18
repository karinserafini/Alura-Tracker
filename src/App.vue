<template>
  <main class="columns is-galpes is-multiline" :class="{ 'dark-mode':activeDarkMode}">
    <div class="columns is-one-quarter ">
      <LateralMenu @theChangedTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter container">
      <FormularioTarefa @WhenSavingTask="saveTask"/>
      <div class="list">
        <BoxComponent v-if="listIsEmpty">
        Você ainda não criou nenhuma tarefa! 
      </BoxComponent>
        <ListaTarefas v-for="(task, index) in tasks" :key="index" :task="task"/>

      </div>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import LateralMenu from './components/LateralMenu.vue';
import ListaTarefas from './components/ListaTarefas.vue';
import ITarefa from './interfaces/ITarefa'
import BoxComponent from './components/BoxComponent.vue';

export default defineComponent({
    name: "App",

    components: {
    LateralMenu,
    FormularioTarefa,
    ListaTarefas,
    BoxComponent,
    },

    data (){
      return {
        tasks: [] as ITarefa[],
        activeDarkMode: false
      }
    },
    
    computed: {
      listIsEmpty () :boolean {
        return this.tasks.length === 0
      }
    },

    methods: {
      saveTask(task: ITarefa) {
        this.tasks.push(task)
      },
      changeTheme(activeDarkMode: boolean) {
        this.activeDarkMode = activeDarkMode
      }
    },

});


</script>

<style>

  .list {
    padding: 1.25rem;
  }

  main {
    --bg-primary: #f2f2f2;
    --text-primary: #f2f2f2;
  }

  main.dark-mode {
    --bg-primary: #2b2b2b;
    --text-primary: #f2f2f2;
  }

  .container {
    background-color: var(--bg-primary);
  }
</style>
