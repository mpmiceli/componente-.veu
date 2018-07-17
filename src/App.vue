<template>
  <div id="app" class="container">
    <div class="jumbotron">
       <arreglo :multiple="true" v-on:changed="viewnewdata" v-bind:TiposCobertura="TiposCobertura"></arreglo>
    </div>
 </div>
</template>

<script>
import arreglo from './ArregloIntermedio.vue'

  export default {
    components : {
      arreglo
    },
    data () {
      return {
        TiposCobertura: [
          {
            texto: 'Tipo de cobertura A'
          },
          {
            texto: 'Tipo de cobertura B'
          },
          {
            texto: 'Tipo de cobertura C'
          },
          {
            texto: 'Tipo de cobertura D'
          },
          {
            texto: 'Tipo de cobertura E'
          }
        ],
      }
    },
    methods: {
      viewnewdata (value) {
        console.log(value);
        
      }
    }
  }
</script>

<style>

</style>
