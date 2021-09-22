<template>
  <Header />
  <nav-bar />
  <div class="container">
    <router-view />
    <Documentacion />
  </div>
</template>

<script>
import { mapActions } from "vuex";
import NavBar from "@/components/NavBar.vue";
import Header from "@/components/Header.vue";
import Documentacion from '@/components/Documentacion.vue'
export default {
  components: {
    NavBar,
    Header,
    Documentacion,
  },
  methods: {
    ...mapActions(["cargarLocalStorage"]),
  },
  created() {
    this.cargarLocalStorage();
  },
};
</script>
