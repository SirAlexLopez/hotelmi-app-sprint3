<template>
  <div>
    <h2>informacion general Reservas</h2>
    <table>
      <tr>
        <th>id</th>
        <th>nombre</th>
        <th>fecha entrada</th>
        <th>fecha salida</th>
        <th>cantidad noches</th>
        <th>tipo hab</th>
        <th>habitacion</th>
        <th>cantidad de personas</th>
        <th>valor</th>
      </tr>
      <tr v-for="reserve in reservas" v-bind:key="reserve.id">
        <td>{{ reserve.id }}</td>
        <td>{{ reserve.quien_reserva }}</td>
        <td>{{ reserve.fecha_entrada }}</td>
        <td>{{ reserve.fecha_salida }}</td>
        <td>{{ reserve.numero_noches }}</td>
        <td>{{ reserve.tipo_habitacion }}</td>
        <td>{{ reserve.numero_habitacion }}</td>
        <td>{{ reserve.numero_personas }}</td>
        <td>{{ reserve.precio }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "VerReservas",
  data: function() {
    return {
      reservas: []
    };
  },
  beforeCreate: function() {
    axios
      .get("http://127.0.0.1:8000/reservas/")
      .then(respuesta => {
        this.reservas = respuesta.data;
      })
      .catch(error => {
        console.log(error);
        alert("Error en la peticion con codigo" + error.response.status);
      });
  }
};
</script>

<style scoped></style>
