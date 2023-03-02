<template>
  <!-- <div> -->
  <nav
    class="navbar navbar-expand-lg"
    :style="`background-color: ${configuracionPagina.menuColor}`"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">{{ configuracionPagina.marca }}</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li
            class="nav-item"
            v-for="(item, index) in configuracionPagina.menus"
            :key="index"
          >
            <a class="nav-link" aria-current="page" href="#">{{
              item.etiqueta
            }}</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- </div> -->
</template>
<script>
export default {
  name: "Menu",
  props: ["inconfiguracion"],
  emits: ["on-configuracion"],
  data() {
    return {
      configuracionPagina: {
        marca: "",
        menuColor: "",
        footerColor: "",
        precioEstilos: "",
        menus: [
          {
            etiqueta: "",
            url: "",
          },
          {
            etiqueta: "",
            url: "",
          },
        ],
      },
    };
  },
  methods: {},
  mounted() {
    this.configuracionPagina = this.inconfiguracion;
  },
};
</script>
