<!-- Representa el html (Estructura) -->
<template>
  <div id="app">
      <h1>Hotel Mintic</h1>
      <h2>Hotelmintic@gmail.com 300123456</h2>
        <nav>
          <button v-on:click="verreservas" > Consultar reserva </button> 
          <button v-on:click="agregarreservas" > Agregar Reserva </button>
          <button v-on:click="borrarreservas" > Borrar Reserva </button>
          <router-view></router-view>
        </nav>
      </div>
</template>

<!-- Representa el js (Comportamiento) -->
<script>
import AgregarReserva from "./components/AgregarReserva";
import VerReservas from "./components/VerReservas";
import EliminarReserva from "./components/EliminarReserva";
  export default {
    name: 'App',
    components: { AgregarReserva, VerReservas, EliminarReserva},
    
    methods: {
      verreservas: function(){
        if(this.$route.name != "verReservas"){
          this.$router.push({name: "verReservas"})
      }  

    },

      agregarreservas: function(){
        if(this.$route.name != "agregarReserva"){
          this.$router.push({
            name:"agregarReserva", 
            params:{dato: "Dato creado"}})
          }
      },

      borrarreservas: function(){
        if(this.$route.name != "borrarReservas"){
          this.$router.push({
            name:"borrarReservas", 
            params:{dato: "Dato eliminado"}})
          }
      },
    },
};
</script>

// Representa el css (estilo) -->
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
