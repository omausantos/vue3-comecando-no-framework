<template>
    <button class="button" @click="aoClicar" :disabled="cronometroRodando">
        <span class="icon">
            <i class="fas" :class="icone"></i>
        </span>
        <span>{{ textoBotao }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'TemporizadorBotao',
    props: {
        textoBotao: {
            type: String,
            required: true
        },
        icone: {
            type: String,
            required: true
        },
        cronometroRodando: {
            type: Boolean
        }
    },
    emits: ['aoClicar'],
    methods: {
        aoClicar(): void {
            this.$emit('aoClicar');
        }
    }
})
</script>
