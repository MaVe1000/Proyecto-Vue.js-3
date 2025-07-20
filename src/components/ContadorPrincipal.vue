<template>
  <body>
    <header>
      <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

      <h1>Contador Vue 3</h1>
      <!-- Aquí va el valor del contador -->
      <div class="counter">
        <p>{{ contador }}</p>
      </div>

      <nav>
        <!-- Botón para incrementar -->
        <button @click="incrementar">Incrementar</button>
        <!-- Botón para decrementar -->
        <button @click="decrementar">Decrementar</button>
        <!-- Botón para reiniciar -->
        <button @click="reiniciar">Reiniciar</button>
      </nav>
    </header>
  </body>
</template>

<script setup>
import { ref } from "vue";
const contador = ref(0);

const incrementar = () => {
  contador.value++;
};
const decrementar = () => {
  contador.value--;
};
const reiniciar = () => {
  contador.value = 0;
};
</script>

<style scoped>
body {
  margin: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--color-text);
  background-color: var(--color-background);
}

header {
  line-height: 1.5;
  max-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 2rem;
}
div.counter {
  border: solid 2px var(--color-border);
  border-radius: 8px;
  width: fit-content;
  margin-top: 1rem;
  box-shadow: 0 4px 6px rgba(5, 77, 20, 0.778);
}
p {
  text-align: center;
  margin: 20px;
  color: var(--color-text);
  font-size: 1.2rem;
  border: 1px solid var(--color-border);
  padding: 1rem;
  border-radius: 8px;
  width: 200px;
  box-shadow: 0 4px 6px rgba(5, 77, 20, 0.778);
}
button {
  background-color: #132a13;
  color: var(--color-button-text);
  border: solid 2px var(--color-border);
  padding: 1rem;
  margin: 1.5rem;
  cursor: pointer;
  font-size: 1rem;
}
button:hover {
  background-color: #008000;
  transition: background-color 0.5s ease;
  translate: 0 0.1rem;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
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
}
</style>
