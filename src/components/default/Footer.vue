<script setup lang="ts">
import { ref } from 'vue';

const year = ref(new Date().getFullYear());

</script>

<template>
  <div>
    <p>Feito por Guilherme Yamasaki - 2010 - {{ year }}</p>
  </div>
</template>


