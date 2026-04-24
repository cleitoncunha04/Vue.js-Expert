<script setup>
defineProps({
    pageTitle: {
        type: String,
        default: 'Page Title'
    },
})
</script>

<template>
    <main class="p-10">
        <h1 class="text-2xl">
            <!-- <slot name="page-title"></slot> -->
             {{ pageTitle }}
        </h1>
        <div class="mt-4">
            <slot></slot>
        </div>
    </main>
</template>