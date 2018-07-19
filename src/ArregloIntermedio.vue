<template>
  <div>
    <form v-if=" multiple" >
       <ul v-for="tipos in TiposCompletos">
          <input type="checkbox" id="info" v-bind:value="tipos.data" v-model="tipos.checked">
              <label for="tipos.data"> {{tipos.data}} </label>
              <div v-if='tipos.checked'>
                <input type="text" class="form-control" placeholder="" value="" v-model='tipos.dato'>
              </div> 
       </ul>
    </form>


    <form v-else >
       <ul v-for="(tipos, indice) in TiposCompletos">
          <input type="radio" id="info" name="datos" v-bind:value="tipos.data" v-model="tiporadio">
              <label for="tipos.data"> {{tipos.data}} </label>
              <div v-if='tiporadio === tipos.data'>
                <input type="text" class="form-control" placeholder="" value="" v-model='tipos.dato'>
              </div> 
       </ul>
    </form>


  </div>
</template>


<script>
  export default {
    props : [
      'TiposCobertura',
      'multiple'
    ],
    data () {
      return {
        TiposCompletos: [
        
        ],
        tiporadio: null,
      }
    }, 
    methods : {
      agregar(){
        this.TiposCobertura.forEach(element => {
              this.TiposCompletos.push({
              data : element.texto,
              dato : '',
              checked : false,
            })
        });
      },
      agregarFinal(){
        var TiposFinales = [];
        if(this.multiple){
          this.TiposCompletos.forEach(element => {
            if(element.checked == true && element.dato>0 && element.dato!=null){
                TiposFinales.push({
                data : element.data,
                dato : element.dato,
              })
            }
          });
        }
        else {
          
          this.TiposCompletos.forEach(element => {
            if(element.checked != null && element.dato>0 && element.dato!=null){
                if(this.tiporadio === element.data){
                TiposFinales.push({
                data : element.data,
                dato : element.dato,
                })
              }
            }
          });
        }
        return TiposFinales;
      }
    },
    mounted(){
      this.agregar();
    },
    watch : {
      TiposCompletos: {
        handler: function(newValue){
          this.$emit('changed', this.agregarFinal());
        },
        deep:true
      }
    }
      
}
</script>
