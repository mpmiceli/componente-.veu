<template>
  <div id="app" class="container">
    <div class="jumbotron">
       <arreglo :multiple="true" :readonly="true" v-on:changed="viewnewdata" v-bind:TiposCobertura="TiposCobertura"></arreglo>
    </div>
 </div>
</template>

<script>
import arreglo from './Formulario.vue'

  export default {
    components : {
      arreglo
    },
    data () {
      return {
        TiposCobertura: [
          {
            valor: 1,
            texto: 'Tipo de cobertura A'
          },
          {
            valor: 2,
            texto: 'Tipo de cobertura B'
          },
          {
            valor: 3,
            texto: 'Tipo de cobertura C'
          },
          {
            valor: 4,
            texto: 'Tipo de cobertura D'
          },
          {
            valor: 5,
            texto: 'Tipo de cobertura E'
          }
        ],
      }
    },
    methods: {
      viewnewdata (value) {
        console.log('arreglo Final:')
        console.log(value);
        
      }
    }
  }
</script>

<style>

</style>

