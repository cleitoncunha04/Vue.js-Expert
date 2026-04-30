<script setup>
import Navbar from '@/components/Navbar.vue';
import { RouterView } from 'vue-router'
import { provide } from 'vue';

provide('message', 'Olá, Curso Vue.js...')

</script>

<template>
    <Navbar />
    <RouterView />
</template>