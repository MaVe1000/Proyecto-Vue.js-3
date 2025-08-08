<template>
  <body>
    <main>
      <!-- Sección contador -->
      <section class="counter-section">
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

        <h1>Contador Vue 3</h1>
        <!-- Aquí va el valor del contador -->
        <div class="counter">
          <p>{{ contador }}</p>
        </div>

        <div>
          <!-- Botón para incrementar -->
          <button @click="incrementar">Incrementar</button>
          <!-- Botón para decrementar -->
          <button @click="decrementar">Decrementar</button>
          <!-- Botón para reiniciar -->
          <button @click="reiniciar">Reiniciar</button>
        </div>
      </section>

      <!-- Sección lista de tareas -->
      <section class="task-section">
        <ListaDeTareas />
        <!-- Aquí se incluye el componente ListaDeTareas -->
      </section>
    </main>
  </body>
</template>

<script setup>
import { ref } from "vue";
import ListaDeTareas from "./ListaDeTareas.vue"; // <-- agregar importación de ListaDeTareas
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
  background-color: #004d00;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  margin: 0.5rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
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
main {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 4rem;
  padding: 2rem;
  flex-wrap: wrap;
  color: #f5f5f5;
  width: 900px;
}
.task-section {
  border: solid 2px var(--color-border);
  border-radius: 8px;
  width: fit-content;
  height: fit-content;
  box-shadow: 0 4px 6px rgba(5, 77, 20, 0.778);
}
.counter-section,
.task-section {
  background-color: #1e1e1e;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 255, 0, 0.2);
  width: 300px;
}

h1 {
  text-align: center;
  margin-bottom: 1rem;
}

.counter {
  font-size: 2.5rem;
  text-align: center;
  margin: 1rem 0;
}

.task-list {
  margin-top: 1rem;
}

.task {
  display: flex;
  justify-content: space-between;
  background-color: #2c2c2c;
  padding: 1rem;
  border-radius: 8px;
  margin-bottom: 0.5rem;
  align-items: center;
}

.task p {
  margin: 0;
  word-wrap: break-word;
  flex-grow: 1;
}

input[type="text"] {
  width: 100%;
  padding: 0.5rem;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  border-radius: 6px;
  border: 1px solid #444;
  background-color: #333;
  color: white;
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
