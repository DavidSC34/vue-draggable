<template>
  <div class="container">
     <h1>vUE drAGAGABLE</h1>
     <button @click="ordenarOriginal" class="btn btn-success" >Reordenar</button>
     <div class="row mt-5">
        <div class="col-6 ">
              <draggable v-model="lista" ghost-class="linea" group="lenguajes" @end="ejecutarAccion">
                  <transition-group type="transition" name="flip">
                      <div class="ordenable" v-for="item in lista " :key="item.id">
                          {{item.id}} {{item.nombre}}
                      </div>
                  </transition-group>
              </draggable>
        </div>
        <div class="col-6">
             <draggable v-model="lista2" ghost-class="linea" group="lenguajes" >
                  <transition-group type="transition" name="flip">
                      <div class="ordenable" v-for="item in lista2 " :key="item.id">
                          {{item.id}} {{item.nombre}}
                      </div>
                  </transition-group>
              </draggable>
        </div>
     </div>
     
    


  </div>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  name: 'HelloWorld',
  components:{
    draggable
  },
  data(){
    return{
      lista:[
        {nombre:'SWIFT',id:1},
        {nombre:'PHP',id:2},
        {nombre:'ANGULAR',id:3},
        {nombre:'JAVA',id:4},
        {nombre:'KOTLIN',id:5},
        {nombre:'PYTHON',id:6},
        {nombre:'JAVASCRIPT',id:7}
        ],
        lista2:[
        {nombre:'LARAVEL',id:8}
        
        ]
    }
  },
  methods:{
    ordenarOriginal(){
          this.lista = this.lista.sort((uno, dos)=>{
                return uno.id - dos.id;
          });
          this.lista2 = this.lista2.sort((uno, dos)=>{
                return uno.id - dos.id;
          });
    },
    ejecutarAccion(){
      alert('Moviste un item');
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.ordenable{
  width: 100%;
  background-color: whitesmoke;
  padding: 10px;
  margin-bottom:2px;
  cursor: move;
}
/*efecto de transicion de elementos al mover */
.flip-move{
  transition: transform 0.5s;
}
/*efecto  o estilo que indica que movemos un objeto */
.linea{
  border-left:10px solid red;
}
</style>
