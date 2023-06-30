<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Profile from './components/default/Profile.vue'
import Footer from './components/default/Footer.vue'
import { ref, onMounted } from 'vue';
import { onUnmounted } from 'vue';

//verificar o mouted no lugar desse DOMContentLoaded
//virtual dom

const period = ref('')
const formattedDateTime = ref('')

const updateCurrentDate = () => {
  const currentDate = new Date();

  formattedDateTime.value = currentDate.toLocaleDateString(undefined, {
    weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: 'numeric', minute: 'numeric', second: 'numeric'
  });

  // verifica se é de dia, noite ou tarde
  const hour = currentDate.getHours();

  if (hour >= 5 && hour < 12) {
    period.value = 'Manhã';
  }

  if (hour >= 12 && hour < 18) {
    period.value = 'Tarde';
  }

  if (hour >= 18 && hour < 24) {
    period.value = 'Noite';
  }

  if (hour >= 0 && hour < 5) {
    period.value = 'Madrugada';
  }
};

// Inicia o loop a cada 1 segundo ao montar o componente
onMounted(() => {
  setInterval(updateCurrentDate, 1000);
});

// Limpa o intervalo quando o componente é desmontado
// onUnmounted(() => {
//   clearInterval(updateCurrentDate);
// });



</script>

<template>
  <header>
    <div id="clock">
      {{ formattedDateTime }}
    </div>

    <div class="profile-image">
      <img alt="Guilherme Image" class="rounded-image" src="@/assets/profile.jpg" width="200" height="200" />
    </div>

    <div class="wrapper">
      <Profile id="greeting" :msg="`Boa ${period}`" />

      <nav>
        <RouterLink to="/">Início</RouterLink>
        <RouterLink to="/contact">Contato</RouterLink>
        <RouterLink to="/about">Currículo</RouterLink>
        <RouterLink to="/about">Outros</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />

  <Footer />

</template>

<!-- remove the scoped from the style tag -->
<style scoped lang="scss">
header {
  line-height: 1.5;
  max-height: 100vh;
  display: flex;
  align-content: space-between;
  & .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    flex: 1;
  }
}

.profile-image {
  display: flex;
  margin-right: 2rem;
}

#clock {
  position: fixed;
  top: 0;
  left: 0;
  padding: 1rem;
  font-size: 20px;
  font-weight: bold;
}


nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    padding: 1rem 0;
    margin-top: 1rem;
  }

  .rounded-image {
  border-radius: 50%;
  }

}
</style>
