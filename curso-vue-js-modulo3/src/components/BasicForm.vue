<template>
    <div class="card w-96 bg-base-100 card-xs shadow-sm mt-10">
        <div class="card-body">
            <h2 class="card-title">Cadastro Simples</h2>
            <div>
                <fieldset class="fieldset">
                    <legend class="fieldset-legend">Nome</legend>
                    <input type="text" class="input w-full" v-model="nameModel" />
                </fieldset>
                <fieldset class="fieldset">
                    <legend class="fieldset-legend">Idade</legend>
                    <input type="text" class="input w-full" v-model="ageModel" />
                </fieldset>
                <pre>
          {{ nameModel }}
          {{ ageModel }}
        </pre>
            </div>
            <div class="justify-end card-actions">
                <button class="btn btn-primary" @click="sendForm">Cadastrar</button>
            </div>
        </div>
    </div>
</template>

<script setup>
const nameModel = defineModel('name', {type: String})

const ageModel = defineModel('age', {type: String})

const emit = defineEmits(['send-form'])

function sendForm() {
    emit('send-form')
}

</script>