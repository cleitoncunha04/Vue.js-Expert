<script setup>
import PageDefault from '@/components/PageDefault.vue';
import { ref } from 'vue';

const count = ref(1);
</script>

<template>
  <PageDefault :page-title="`Home Page: ${count}`">
    <!-- <template #page-title>
      Home Page
    </template> -->
    <div>
      <button class="btn btn-primary" @click="count++">+</button>
    </div>
    <p>
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Itaque atque at accusantium culpa sint id ipsam provident? Reprehenderit minima qui cum magnam cumque maiores delectus ut quas, est, beatae rem.
    </p>
  </PageDefault>
</template>
