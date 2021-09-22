<template>
  <form @submit.prevent="procesarFormulario">
    <Input :tarea="tarea" />
  </form>
  <hr />

  <lista-tareas />
</template>

<script>
import Input from "@/components/Input";
import ListaTareas from "@/components/ListaTareas";
import { mapActions } from "vuex";
const shortid = require("shortid");

export default {
  name: "Home",
  components: { Input, ListaTareas },
  data() {
    return {
      tarea: {
        id: "",
        nombre: "",
        categorias: [],
        estado: "",
        numero: 0,
      },
    };
  },
  methods: {
    ...mapActions(["setTareas"]),

    procesarFormulario() {
      console.log(this.tarea);
      if (this.tarea.nombre.trim() === "") {
        console.log("vacío");
        return;
      }
      console.log("No está vacío");

      //Generar id
      this.tarea.id = shortid.generate();

      //Envían datos
      this.setTareas(this.tarea);

      this.tarea = {
        id: "",
        nombre: "",
        categorias: [],
        estado: "",
        numero: 0,
      };
    },
  },
};
</script>
