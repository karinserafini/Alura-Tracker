<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="logo-alura-tracker">
        </h1>
        <Button class="button" @click="alterTheme">
            {{ buttonText }}
        </Button>
    </header>

</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'LateralMenu',

    emits:['theChangedTheme'],
   
    data() {
        return {
            activeDarkMode: false
        }
    },

    computed: {
        buttonText() {
            if (this.activeDarkMode) {
                return 'Desativar Modo Escuro'
            }
            return "Ativar Modo Escuro"
        }
    },

    methods: {
        alterTheme() {
            this.activeDarkMode= !this.activeDarkMode
            this.$emit('theChangedTheme', this.activeDarkMode)
        }
    }
})
</script>
<style scoped >
header {
    padding: 1rem;
    background-color: #64b6ac;
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>