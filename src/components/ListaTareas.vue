<template>
  <h2 class="text-center">Tus Tareas</h2>
  <table class="table">
    <thead class="table-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Nombre</th>
        <th scope="col">Categoría</th>
        <th scope="col">Relevancia</th>
        <th scope="col">Número</th>
        <th scope="col">Acción</th>
      </tr>
    </thead>
    <tbody>
      <tr class="table-primary" v-for="item in tareas" :key="item.id">
        <th scope="row">{{ item.id }}</th>
        <td>{{ item.nombre }}</td>
        <td>
          <span v-for="(cat, index) in item.categorias" :key="index">
            {{ cat}}
          </span>
        </td>
        <td>{{ item.estado }}</td>
        <td>{{ item.numero }}</td>
        <td>
          <button
            v-on:click="deleteTareas(item.id)"
            class="btn btn-danger btn-sm"
          >
            Eliminar
          </button>
          <router-link
          class="btn btn-warning ml-2 btn-sm"
          :to="{
            name: 'Editar',
            params: {
              id: item.id
            }
            }"
          >
            Editar
          </router-link>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import { mapState, mapActions } from "vuex";
export default {
  methods: {
    ...mapActions(["deleteTareas"]),
  },
  computed: {
    ...mapState(["tareas"]),
  },
};
</script>
