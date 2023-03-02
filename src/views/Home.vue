<template>
  <div class="home">
    
    <p>Daniel Mauricio Villarte</p>
    <p>Rudy Roger Zepita</p>
    <p>Sandra Severich</p>
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Menu
      :inconfiguracion="configuracionPagina"
      @on-configuracion="cargarConfiguracion($event)"
    ></Menu>
    <Producto ></Producto>
    <ProductosRelacionados ></ProductosRelacionados>
    <Footer :incolorFooter="configuracionPagina.footerColor" @on-colorFooter="cargarColor($event)"></Footer>
  </div>
</template>

<script>
// @ is an alias to /src
// import Menu from "@/components/Menu.vue";
import Menu from "@/components/Menu.vue";
import Producto from "@/components/Producto.vue";
import ProductosRelacionados from "@/components/ProductosRelacionados.vue";
import Footer from "@/components/Footer.vue";
export default {

  name: "Home",
  mounted() {
    // this.cargarProductos();
  },
  data() {
    return {
      configuracionPagina: {
        marca: "MegaDron",
        menuColor: "lightblue",
        footerColor: "slategrey",
        precioEstilos: "background: orangered; color: white; font-weight: bold",
        menus: [
          {
            etiqueta: "Inicio",
            url: "?",
          },
          {
            etiqueta: "Tienda",
            url: "?",
          },
        ],
      },
      producto: {},
      productos: [],
    };
  },
  methods: {
    
  },
  components: {
    Menu,
    Producto,
    ProductosRelacionados,
    Footer,
  },
};
</script>
<style scoped>
.color-box {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin: 7px;
  display: inline-block;
}

.clic {
  cursor: pointer;
}

.quantity button {
  border-radius: 50%;
  display: inline-block;
  width: 30px;
}

.quantity div {
  text-align: center;
  min-width: 30px;
  display: inline-block;
  font-weight: bold;
}

.buy-box {
  margin: 20px;
}

footer {
  text-align: center;
  padding: 30px 10px;
  margin-top: 50px;
  min-height: 100px;
}

.container {
  margin-top: 50px;
}

.producto-relacionado-precio {
  background: orangered;
  color: white;
  text-align: center;
  padding: 10px;
}
</style>