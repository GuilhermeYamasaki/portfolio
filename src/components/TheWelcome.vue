<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import { ref, computed } from 'vue';

const dataNascimento = ref('1998-09-04');
const hoje = ref(new Date());

const idade = computed(() => {
  const dataNascimentoValue = new Date(dataNascimento.value);
  const hojeValue = hoje.value;

  let idade = hojeValue.getFullYear() - dataNascimentoValue.getFullYear();
  const mesAtual = hojeValue.getMonth();
  const diaAtual = hojeValue.getDate();
  const mesNascimento = dataNascimentoValue.getMonth();
  const diaNascimento = dataNascimentoValue.getDate();

  if (mesAtual < mesNascimento || (mesAtual === mesNascimento && diaAtual < diaNascimento)) {
    idade--;
  }

  return idade;
});
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>

    <template #heading>Quem sou eu ?</template>

    <p>
      Meu nome é Guilherme Yuji Yamasaki.
    </p>
    <p>
      Tenho {{ idade }} anos e sou de Araçatuba-SP.
    </p>
    <p>
      2 anos de experiência na área como Desenvolvedor Web.
    </p>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Profissão</template>

    <p>
      Desenvolvedor Full Stack
    </p>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Passatempo</template>

    <p>
      Gosto de jogar Xadrez e de jogar online quando tenho tempo. 
      Ávido leitor de livros e apreciador da cultura japonesa.
    </p>
    
  </WelcomeItem>
</template>
