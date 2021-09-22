<template>
  <h1>Editar</h1>
  {{ $route.params.id }} - {{ tarea }}

  <form @submit.prevent="updateTarea(tarea)">
    <Input :tarea="tarea" />
  </form>
</template>

<script>
import Input from "@/components/Input";
import { mapState, mapActions } from "vuex";
export default {
  components: { Input },
  methods: {
    ...mapActions(["setTarea", "updateTarea"]),
  },
  computed: {
    ...mapState(["tarea"]),
  },
  created() {
    this.setTarea(this.$route.params.id);
  },
};
</script>
