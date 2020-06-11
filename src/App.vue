<template>
  <div id="app">
  <h1>Binarizacion de Imagen en Paralelo</h1>
    <div v-for="image in datos" v-bind:key="image.foto_modificada" class="container">
      <div class="first-column">
        <p>Altura original: {{ image["original-height"] }}</p>
        <p>Ancho original: {{ image["original-width"] }}</p>
        <p>Numero de pods: {{ image["num-pods"] }}</p>
        <p>Alto por pod: {{ image["height-per-pod"] }}</p>
        <p>Ancho por pod: {{ image["width-per-pod"] }}</p>
        <p>Tiempo de computo: {{ image["compute-time"] }}</p>
      </div>
      <div class="other-column">
        <p>Foto original</p>
        <img :src="image.foto_original"/>
      </div>
      <div class="other-column">
        <p>Foto modificada</p>
        <img :src="image.foto_modificada"/>
      </div>
    </div>
  </div>
</template>

<script>
  import { db } from './firebase';

  export default {
    name: 'app',
    data() {
      return {
        datos: [],
      }
    },
    firestore() {
      return {
        datos: db.collection('datos'),
      }
    },
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .container {
    width: 90%;
    background-color: #92e62b;
    margin: auto;
    margin-top: 20px;
    margin-bottom: 20px;
    padding: 10px;
  }
  .first-column, .other-column {
    width: 28%;
    padding-right: 20px;
    padding-left: 20px;
    display: inline-block;
  }
  .other-column img {
    width: 300px;
  }
</style>
