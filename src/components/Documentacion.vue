<template>
  <hr class="mt-5" />
  <section class="explain">
    <div class="row">
      <div class="explain-title col-md-4">
        <h2>Documentación</h2>
      </div>
      <div class="doccard col-md-4">
        <div class="doccard-header">
          <h3>Reto</h3>
        </div>
        <div class="doccard-body">
          <p>
            Generar una aplicación de tareas capaz de almacenar datos de forma
            local y dinámica
          </p>
        </div>
      </div>

      <div class="doccard col-md-4">
        <div class="doccard-header">
          <h3>Herrameintas</h3>
        </div>
        <div class="doccard-body">
          <ul>
            <li>VUE</li>
            <li>VUEX</li>
            <li>idGenerator</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
  <section>
    <h2 class="mt-5">¿Cómo funciona?</h2>
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <h4>La Store de VUEX se encarga de la comunicación entre componentes.</h4>

        <pre><code class="language-js">//State  
  state: {
    tareas: [],
    tarea: {
      id: "",
      nombre: "",
      categorias: [],
      estado: "",
      numero: 0,
    },
  },</code></pre>
        Todos los datos de la aplicación son llevados por el objeto tarea y se
        guadan en el Array tareas

        <pre><code class="language-js">//Acciones
  actions: {
    cargarLocalStorage({ commit }) {
      if (localStorage.getItem("tareas")) {
        const tareas = JSON.parse(localStorage.getItem("tareas"));
        commit("cargar", tareas);
        return;
      }
      localStorage.setItem("tareas", JSON.stringify([]));
    },
    setTareas({ commit }, tarea) {
      commit("set", tarea);
    },
    deleteTareas({ commit }, id) {
      commit("delete", id);
    },
    setTarea({ commit }, id) {
      commit("tarea", id);
    },
    updateTarea({ commit }, tarea) {
      commit("update", tarea);
    },
  },</code></pre>
        Cada Acción desencadena una mutación, que se encargará de una
        característica de la aplicación.

        <pre><code class="language-js">//Mutaciones  
  actions: {
    cargarLocalStorage({ commit }) {
      if (localStorage.getItem("tareas")) {
        const tareas = JSON.parse(localStorage.getItem("tareas"));
        commit("cargar", tareas);
        return;
      }
      localStorage.setItem("tareas", JSON.stringify([]));
    },
    setTareas({ commit }, tarea) {
      commit("set", tarea);
    },
    deleteTareas({ commit }, id) {
      commit("delete", id);
    },
    setTarea({ commit }, id) {
      commit("tarea", id);
    },
    updateTarea({ commit }, tarea) {
      commit("update", tarea);
    },
  },</code></pre>
        Las mutaciones realizan la acción última y modifican la los datos de la
        aplicación.
      </li>
      <li class="list-group-item">
        <h4>Componentes</h4>
        <div>
          <img src="@/assets/components.jpg" class="mr-sm-2 float-sm-left img-fluid" alt="" />
          <ul>
            <li><strong>Input -></strong> Establece el formulario de introducción de datos.</li>
            <li><strong>Lista Tareas -></strong> Muestra los datos introducidos y ya procesados.</li>
            <li>Los demás componentes forman parte del layout y no tienen interés en este proyecto.</li>
          </ul>
        </div>
      </li>
      <li class="list-group-item">
        <h4>Edición de tarea</h4>
        <p>Cuando queremos editar una tarea, capturamos un id generado con idGenerator en el momento de guardar los datos. Este id se pasa a través de la URL de forma dinámica y mostramos la edición con el mismo formulario para esa tarea en específico.</p>

<pre><code class="language-js">
    delete(state, payload) {
      state.tareas = state.tareas.filter((item) => item.id !== payload);
      localStorage.setItem("tareas", JSON.stringify(state.tareas));
    },
    tarea(state, payload) {
      if (!state.tareas.find((item) => item.id === payload)) {
        router.push("/");
        return;
      }
      state.tarea = state.tareas.find((item) => item.id === payload);
    },
    update(state, payload) {
      state.tareas = state.tareas.map((item) =>
        item.id === payload.id ? payload : item
      );
      router.push("/");
      localStorage.setItem("tareas", JSON.stringify(state.tareas));
    },
    </code></pre>
    Mediante los métodos filter, find y map, podemos establecer comparaciones para las tareas de modificar, actualizar y eliminar.

      </li>
      <li class="list-group-item"><h4>Repositorio</h4>
      <a href="#"></a>
      </li>
      <li class="list-group-item">And a fifth one</li>
    </ul>
  </section>
</template>

<script>
import Prism from "@/plugins/prism";
export default {};
</script>

<style>
.doccard {
  background: rgb(53, 53, 53);
  color: rgb(245, 245, 245);
  padding: 2rem;
  border: 3px solid;
}
</style>
