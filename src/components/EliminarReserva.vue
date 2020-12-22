<template>
  <div id="BorrarReserva">
    <h3>Borrar Reserva</h3>
    <label for="id">Id</label>
    <input v-model="id" id="id" />
    <button v-on:click="BorrarReserva">Borrar Reserva</button>
    <p>la reserva con id {{ id }} sera eliminada</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "BorrarReserva",
  data: function() {
    return {
      id: 0
    };
  },
  methods: {
    mostrarId: function() {
      alert(this.id);
    },
    BorrarReserva: function() {
      axios
        .delete('http://127.0.0.1:8000/reserva/borrar/'+this.id)
        .then(respuesta => {
          alert(respuesta.data.mensaje);
        })
        .catch(error => {
          console.log("Error::",error.response.data)
          alert("error en el servidor");
        });
    }
  },
  created: function() {
    this.datoRecibido = this.$route.params.dato;
  }
};
</script>

<style scoped>
#agregarOrden {
  background-color: beige;
}
</style>