<script setup>
import { useRouter } from 'vue-router';

  const router = useRouter()

  function handleAbout() {
    router.push('/about')
  }

</script>

<template>
  <main class="p-10">
    <button class="btn btn-primary" @click="handleAbout()">
      About
    </button>
  </main> 
</template>
