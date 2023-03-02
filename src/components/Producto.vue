<template>
  <div class="container">
    <div class="row">
      <h3>S6S Mini GPS Drones</h3>
    </div>
    <div class="row">
      <div class="col-12 col-sm-6 col-md-4">
        <img :src="`${producto.imagen}`" width="100" style="width: 100%" />
      </div>
      <div class="col-12 col-sm-6 col-md-8">
        <h6 v-html="producto.descripcion"></h6>
        <div class="p-3 mb-2 text-white" :style="precioEstilos">
          Precio: {{ producto.precio }} BOB
        </div>
        <h5>Color</h5>
        <div>
          <div
            v-for="item in producto.colores"
            :key="item.id"
            class="color-box clic"
            :style="`background: ${item}`"
            @click="elegirColor(item)"
          ></div>
        </div>
        <h5>Cantidad</h5>
        <div class="quantity">
          <button @click="restar">-</button>
          <div>{{ contador }}</div>
          <button @click="adicionar">+</button>
        </div>
        <div class="buy-box">
          <button
            type="button"
            class="btn btn-primary"
            :disabled="contador < 1"
            @click="comprar"
            v-if="contador < 1"
          >
            Comprar
          </button>
          <button
            type="button"
            class="btn btn-primary"
            :disabled="contador < 1"
            style="background-color: green"
            @click="comprar"
            v-else
          >
            Comprar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Producto",
  data() {
    return {
      precioEstilos: "background: orangered; color: white; font-weight: bold",
      producto: {},
      contador: 0,
      color: "",
    };
  },
  methods: {
    cargarProducto() {
      
      this.axios.get(process.env.VUE_APP_API + '/productos/' + 1)
      .then((response) => { 
        this.producto = response.data;
       
      })
      .catch((err) => {console.log(err);})
    },
    adicionar() {
      return this.contador++;
    },
    restar() {
      return this.contador > 0 ? this.contador-- : 0;
    },
    elegirColor(c) {
      this.color = c;
    },
    comprar() {
      let pedido = {
        id: this.producto.id,
        cantidad: this.contador,
        color: this.color,
      };
      if (this.color && this.contador > 0)
        alert("pedido " + JSON.stringify(pedido));
      else alert("Debe seleccionar un color y cantidad mayor a 0. !!");
    },
    
  },
  mounted() {
    
    this.cargarProducto();
    
  },
};
</script>

<style scoped lang="scss">
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
</style>
