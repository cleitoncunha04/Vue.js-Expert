<template>
    <h2>Meu componente - Usuário: {{ user }}</h2>
</template>

<script setup>
import { onBeforeMount, onBeforeUnmount, onMounted, onUnmounted, onUpdated, ref } from 'vue';

const id = ref('1234')

const user = ref('')

function requestFake() {
    setTimeout(() => { 
        user.value = 'Glauber'
     }, 2000)
}

onBeforeMount(() => {
    console.log('MyComponent vai ser montado...')
})

onMounted(() => {
    if (!id.value) {
        return
    }

    requestFake()

    console.log('MyComponent foi montado...')
})

onUpdated(() => {
    console.log('MyComponent foi atualizado...')
})

onUnmounted(() => {
    console.log('MyComponent foi desmontado...')
})

onBeforeUnmount(() => {
    console.log('MyComponent vai ser desmontado...')
})
</script>