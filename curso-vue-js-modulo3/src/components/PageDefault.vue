<script setup>
defineProps({
    pageTitle: {
        type: String,
        default: 'Page Title'
    },
})

const emit = defineEmits(['refresh'])

function setRefresh() {
    emit('refresh')
}
</script>

<template>
    <main class="p-10">
        <div class="flex justify-between">
            <h1 class="text-2xl">
                <!-- <slot name="page-title"></slot> -->
                {{ pageTitle }}
            </h1>
            <button class="btn btn-primary btn-outline" @click="setRefresh()">Atualizar</button>
        </div>
        <div class="mt-4">
            <slot></slot>
        </div>
    </main>
</template>