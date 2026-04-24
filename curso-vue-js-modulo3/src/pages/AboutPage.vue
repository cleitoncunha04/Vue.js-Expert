<script setup>
import PageDefault from '@/components/PageDefault.vue';
import { ref } from 'vue';

const aboutTitle = ref('About Page');

function setAboutTitle(title) {
  aboutTitle.value = title;
}
</script>

<template>
  <PageDefault :page-title="aboutTitle">
    <!-- <template #page-title>
      About Page
    </template> -->
    <div class="flex gap-4">
      <button class="btn btn-primary" @click="setAboutTitle('About 01')">Ler About 01</button>

      <button class="btn btn-primary" @click="setAboutTitle('About 02')">Ler About 02</button>

      <button class="btn btn-primary" @click="setAboutTitle('About 03')">Ler About 03</button>
    </div>
  </PageDefault>
</template>