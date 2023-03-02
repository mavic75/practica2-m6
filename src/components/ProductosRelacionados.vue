<template>
  <div class="container">
    <div class="row">
      <h4>Productos relacionados</h4>
    </div>
    <div class="row">
      <div
        class="col"
        v-show="item.id > 1"
        v-for="(item, index) in productosRelacionados"
        :key="index"  
      >
        <div class="card" style="width: 18rem">
          <div class="card-body" @click.prevent="elegirProducto(item)">
            <h5 class="card-title">{{ item.nombre }}</h5>
            <img :src="item.imagen" alt="" width="100%" style="width: 100%" />
            <p class="card-text">{{ item.descripcion }}</p>
            <div class="producto-relacionado-precio">
              Precio:{{ item.precio }} BOB
            </div>
            <div>
              <div>
                <div
                  v-for="(e, index) in item.colores"
                  :key="index"
                  class="color-box"
                  :style="`background: ${e}`"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "ProductosRelacionados",
    data() {
        return {
            productosRelacionados: []
        }
    },
    methods: {
        cargarProductos() {
            this.axios.get(process.env.VUE_APP_API + '/productos/')
            .then((response) => { 
                this.productosRelacionados = response.data;
            })
            .catch((err) => {console.log(err);})
        }, 
        elegirProducto(item) {
            alert(JSON.stringify(item));
        }
    },
    mounted() {
        this.cargarProductos();
    },
};
</script>

<style>
.container {
    margin-top: 50px;
}

.producto-relacionado-precio {
	background: orangered;
	color: white;
	text-align: center;
	padding: 10px;
}
.color-box {
	width: 40px;
	height: 40px;
	border-radius: 50%;
	margin: 7px;
	display: inline-block;
}
</style>
