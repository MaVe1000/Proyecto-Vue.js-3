<template>
  <section class="todo">
    <h2>Lista de Tareas</h2>

    <form @submit.prevent="agregarTarea">
      <input
        v-model="nuevaTarea"
        type="text"
        placeholder="Escribe una tarea"
        required
      />
      <button type="submit">Agregar</button>
    </form>

    <ul>
      <li
        v-for="(tarea, index) in tareas"
        :key="index"
        :class="{ completada: tarea.completada }"
      >
        <span @click="toggleCompletada(index)">
          {{ tarea.texto }}
        </span>
        <button @click="eliminarTarea(index)">Eliminar</button>
      </li>
    </ul>
  </section>
</template>

<script setup>
import { ref, watch, onMounted } from "vue";

const nuevaTarea = ref("");
const tareas = ref([]);

// Cargar tareas del localStorage cuando el componente se monta
onMounted(() => {
  const tareasGuardadas = localStorage.getItem("tareas");
  if (tareasGuardadas) {
    tareas.value = JSON.parse(tareasGuardadas);
  }
});

// Guardar tareas en localStorage cada vez que cambian
watch(tareas, (nuevasTareas) => {
  localStorage.setItem("tareas", JSON.stringify(nuevasTareas));
}, { deep: true });

const agregarTarea = () => {
  if (nuevaTarea.value.trim() === "") return;
  tareas.value.push({ texto: nuevaTarea.value, completada: false });
  nuevaTarea.value = "";
};

const eliminarTarea = (index) => {
  tareas.value.splice(index, 1);
};

const toggleCompletada = (index) => {
  tareas.value[index].completada = !tareas.value[index].completada;
};
</script>

<style scoped>
.todo {
  margin: 2rem auto;
  max-width: 400px;
  padding: 1rem;
  border-top: 2px dashed var(--color-border);
}

.todo h2 {
  text-align: center;
}

.todo input {
  padding: 0.5rem;
  width: 70%;
  margin-right: 0.5rem;
}

.todo ul {
  list-style: none;
  padding: 0;
}

.todo li {
  background: #f9f9f9;
  margin-top: 1rem;
  padding: 0.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 5px;
  color: #050e30;
}

.todo li span {
  cursor: pointer;
}

.todo li.completada span {
  text-decoration: line-through;
  color: gray;
}
</style>