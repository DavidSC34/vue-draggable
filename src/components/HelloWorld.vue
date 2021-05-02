<template>
  <div class="hello">
     <h1>vUE drAGAGABLE</h1>
     <button @click="ordenarOriginal" >Reordenar</button>
     
      <draggable v-model="lista" ghost-class="linea" >
          <transition-group type="transition" name="flip">
              <div class="ordenable" v-for="item in lista " :key="item.id">
                  {{item.id}} {{item.nombre}}
              </div>
          </transition-group>
      </draggable>


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
        ]
    }
  },
  methods:{
    ordenarOriginal(){
          this.lista = this.lista.sort((uno, dos)=>{
                return uno.id - dos.id;
          });
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
