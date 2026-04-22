<script setup>
import { ref, reactive, computed, onMounted, watch, watchEffect } from 'vue'
import MyComponent from './components/MyComponent.vue'

const message = 'Aqui tem uma mensagem!'

const html = '<h1>Título</h1>'

const showElement = false

const ifElement = 'A'

const names = ['Glauber', 'João', 'Maria']

const send = () => alert('Enviado...')

const submitForm = () => alert('Formulário enviado...')

const divClass = 'minha-classe'
const divClass2 = 'minha-classe-2'

const myClass = ref(false)

const myName = ref('Cleiton Cunha')

const age = ref(0)

// setTimeout(() => { myName.value = 'Cleiton Cunha' }, 5000)

const count = ref(0)

console.log(count.value)

count.value++

console.log(count.value)

const person = ref({
  id: 1,
  name: 'Glauber',
  age: 21
})

const state = reactive({ count: 0 })

const student = reactive({
  name: 'Glauber',
  modules: [
    'Módulo 01 - Introdução',
    'Módulo 02 - Fundamentos',
    'Módulo 03 - Componentes'
  ]
})

const studentName = computed(() => student.name)

const hasModules = computed(() => student.modules.length ? 'Sim' : 'Não')

const student2 = ref({
  name: 'Cleiton',
  modules: []
})

const studentName2 = computed(() => student2.value.name)

const hasModules2 = computed(() => student2.value.modules.length ? 'Sim' : 'Não')

onMounted(() => {
  console.log('app onMounted')

  console.log(input.value.focus())
})

const showComponent = ref(true)

const inputName = ref('')

const user = ref('')

const updateUser = () => {
  user.value = inputName.value
}

watch(user, (newUser, oldUser) => {
  console.log('Usuário antigo: ', oldUser)
  console.log('Usuário novo: ', newUser)
})

watch(user, async (newUser) => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${newUser.length > 0 ? newUser.length : 1}`
  )

  let data = {}

  data.value = await response.json()

  console.log(data.value)
}, { immediate: true })

watchEffect(async () => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${user.value.length > 0 ? user.value.length : 1}`
  )

  let data = {}

  data.value = await response.json()

  console.log(data.value)
})

const input = ref(null)

console.log(input.value)

const focusNext = () => {
  if (!input.value) return

  input.value.focus()
}

</script>

<template>
  <div v-if="false">
    <ul>
      <li>
        <h2>v-text</h2>
        <p v-text="message"></p>
      </li>

      <li>
        <h2>v-html</h2>
        <p v-html="html"></p>
      </li>

      <li>
        <h2>v-show</h2>
        <p v-show="showElement">Elemento exibido no v-show</p>
      </li>

      <li>
        <h2>v-if / v-else</h2>
        <p v-if="ifElement === 'A'">Elemento exibido com v-if (A)</p>
        <p v-else-if="ifElement === 'B'">Elemento exibido com v-else-if (B)</p>
        <p v-else>Elemento exibido com v-else</p>
      </li>

      <li>
        <h2> v-for</h2>
        <p v-for="(name, index) in names" :key="index">{{ name }} - {{ index + 1 }}</p>
      </li>

      <li>
        <h2>v-in - Abreviado @</h2>
        <button @click="send">Enviar</button>
        <form @submit.prevent="submitForm">
          <input type="text" @keyup.enter="submitForm">
            <button type="submit">Enviar formulário</button>
        </form>
      </li>

      <li>
        <h2>v-bind - Abreviado: :</h2>
        <div :class="myClass ? divClass : divClass2">Elemento com classe</div>
        <button @click="myClass = !myClass">Mudar classe</button>
      </li>

      <li>
        <h2>v-model</h2>
        <input type="text" v-model.trim="myName" placeholder="Informe o seu nome...">
          <p v-if="myName !== ''">Olá, {{ myName }}...</p>
          <input type="text" v-model.number="age" placeholder="Informe a sua idade">
            <p v-if="age > 0">Você tem {{ age }} anos...</p>
      </li>

      <li>
        <h3>v-pre</h3>
        <p v-pre>{{ myName }}</p>
      </li>

      <li>
        <h3>v-once</h3>
        <p v-once>{{ myName }}</p>
      </li>
    </ul>
  </div>

  <div v-if="false">
    <p>{{ count }}</p>
    <button @click="count++">+</button>
    <button @click="count--">-</button>
    <p>{{ person }}</p>
    <input type="text" v-model="person.name">
      <p>{{ state.count }}</p>
  </div>

  <div v-if="false">
    <h2>computed properties</h2>
    <p>{{ studentName }}</p>
    <p>Possui módulos liberados: {{ hasModules }}</p>
    <br>
    <p>{{ studentName2 }}</p>
    <p>Possui módulos liberados: {{ hasModules2 }}</p>
  </div>

  <div v-if="false">
    <button @click="showComponent = !showComponent">Mostrar componente</button>
    <MyComponent v-if="showComponent" />
  </div>

  <form @submit.prevent="updateUser()" v-if="false">
    <input type="text" v-model="inputName" placeholder="Informe o usuário...">
      <button type="submit">Atualizar usuário</button>
  </form>

  <div>
    <input type="text" @keydown.tab.prevent="focusNext">
      <button>Ok</button>
      <input type="text" ref="input">
  </div>
</template>

<style>
.minha-classe {
  border: 1px solid blue
}

.minha-classe-2 {
  border: 1px solid red
}
</style>
