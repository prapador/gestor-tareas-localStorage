<template>
  <h4 class="mt-4">Nombre tarea</h4>
  <input
    v-model.trim="tarea.nombre"
    type="text"
    class="form-control my-2"
    placeholder="Ingrese Nombre"
  />

  <!-- Categoria -->
  <!-- <div class="form-check form-check-inline">
    <input
      v-model="tarea.categorias"
      class="form-check-input"
      type="checkbox"
      id="inlineCheckbox1"
      value="javascript"
    />
    <label class="form-check-label" for="inlineCheckbox1">JavaScript</label>
  </div>

  <div class="form-check form-check-inline">
    <input
      v-model="tarea.categorias"
      class="form-check-input"
      type="checkbox"
      id="inlineCheckbox2"
      value="node js"
    />
    <label class="form-check-label" for="inlineCheckbox2">Node.js</label>
  </div> -->

  <hr />

  <!-- Prioridad -->
  <h4>Prioridad</h4>
  <!-- Radio1 -->
  <div class="mt-2">
    <div class="form-check form-check-inline">
      <input
        v-model="tarea.estado"
        class="form-check-input"
        type="radio"
        name="inlineRadioOptions"
        id="inlineRadio1"
        value="urgente"
      />
      <label class="form-check-label" for="inlineRadio1">Urgente</label>
    </div>

    <!-- Radio 2 -->
    <div class="form-check form-check-inline">
      <input
        v-model="tarea.estado"
        class="form-check-input"
        type="radio"
        name="inlineRadioOptions"
        id="inlineRadio2"
        value="Importante"
      />
      <label class="form-check-label" for="inlineRadio2">Importante</label>
    </div>

    <!-- Radio 3 -->
    <div class="form-check form-check-inline">
      <input
        v-model="tarea.estado"
        class="form-check-input"
        type="radio"
        name="inlineRadioOptions"
        id="inlineRadio3"
        value="Baja"
      />
      <label class="form-check-label" for="inlineRadio3">Baja</label>
    </div>
  </div>

<hr>

  <!-- categoria -->
  <h4> Categoría</h4>
  <div class="mt-2">
    <input v-model="tarea.categorias" type="text" class="form-control" />
  </div>

<hr>

  <!-- numer -->
  <h4>Relevancia (número)</h4>
  <div class="mt-2">
    <input v-model.number="tarea.numero" type="number" class="form-control" />
  </div>

  <button
    type="submit"
    class="btn btn-dark mt-5 btn-block"
    :disabled="bloquear"
  >
    {{ buttonName }}
  </button>
</template>

<script>
export default {
  props: {
    tarea: Object,
  },
  computed: {
    bloquear() {
      return this.tarea.nombre.trim() === "" ? true : false;
    },
    buttonName() {
      return this.$route.path === "/" ? "Añadir" : "Editar";
    },
  },
};
</script>
