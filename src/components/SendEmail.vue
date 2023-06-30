<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'


</script>

<template>
    <WelcomeItem>
        <template #icon>
            <DocumentationIcon />
        </template>

        <input type="text" placeholder="Nome" class="form-group"/>
        <input type="text" placeholder="Email" class="form-group"/>
        <input type="text" placeholder="Assunto" class="form-group"/>
        <textarea placeholder="Mensagem" class="form-group"></textarea>
        <button class="form-group">Enviar</button>


    </WelcomeItem>
</template>

<style scoped>

.form-group {
  margin-bottom: 0.25rem;
  display: flex;
  flex-direction: column;
  width: 300px;
  padding: 0;
}

.form-group textarea {
  height: 500px;
}




</style>