<script setup>
import PageDefault from '@/components/PageDefault.vue';
import { ref } from 'vue';
import BasicForm from '@/components/BasicForm.vue';

const count = ref(1);

const isLoading = ref(false)

function handleGetApi() {
  isLoading.value = true

  setTimeout(() => {
    isLoading.value = false
  }, 3000)
}

const form = ref({
  name: '',
  age: '',
})

function setBasicProfile() {
  form.value.name = 'Cleiton Cunha'
  form.value.age = '21'
}

function sendForm() {
  alert(`Formulário enviado com sucesso (${form.value.name} - ${form.value.age} anos)...`)
}
</script>

<template>
  <PageDefault :page-title="`Home Page: ${count}`" @refresh="handleGetApi">
    <!-- <template #page-title>
      Home Page
    </template> -->
    <div v-if="isLoading" class="text-center">
      <span class="loading loading-spinner loading-lg"></span>
    </div>

    <div v-else>
      <div>
        <button class="btn btn-primary" @click="count++">+</button>
      </div>
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Itaque atque at accusantium culpa sint id ipsam
        provident?
        Reprehenderit minima qui cum magnam cumque maiores delectus ut quas, est, beatae rem.
      </p>

      <button class="btn btn-primary" @click="setBasicProfile">Perfil padrão</button>

      <BasicForm @send-form="sendForm" v-model:name="form.name" v-model:age="form.age" />

    </div>
  </PageDefault>
</template>
