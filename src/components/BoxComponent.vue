<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'BoxComponent',
})
</script>


<style scoped>
.box {
    background-color: #2ec4b6;
    color: #edf2f4;
}
</style>