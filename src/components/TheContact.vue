<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import SendEmail from './SendEmail.vue'


</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>

    
    <template #heading>Contato</template>
    <ul>
      <li>
        <a href="https://www.linkedin.com/in/guilherme-yamasaki" target="_blank">Linkedin</a>
      </li>
      <li>
        <a href="https://www.github.com/guilhermeyamasaki" target="_blank">Github</a>
      </li>
      <li>
        <a href="https://www.instagram.com/guilhermeyamasaki" target="_blank">Instagram</a>
      </li>
      <li>
        <a href="https://www.facebook.com/guilhermeyamasaki" target="_blank">Facebook</a>
      </li>
    </ul>
  
  </WelcomeItem>

  <WelcomeItem>
    <template #heading>Gostou do meu perfil ? Envie um email</template>
    <SendEmail />
  </WelcomeItem>
  

</template>

