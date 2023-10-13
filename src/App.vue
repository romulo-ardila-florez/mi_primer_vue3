<script setup>  
import {ref, computed} from 'vue'
const saludo =" Hola Mundo Programa Dos";
const valor = ref (0);
const incrementar =() =>  (valor.value ++) ; 
const disminuir =() => {  
    (valor.value --);
};
const resert =() => (valor.value = 0) ;

const cambioColor = computed(() =>{
  if(valor.value === 0){
    return "neutro";
  }
  if(valor.value > 0 ){
    return "positive";
  }
  if(valor.value < 0){
    return "negative";
  }
});
const arrayNuevo =ref([]);
const add =() =>{
  arrayNuevo.value.push(valor.value);
};

const disableBoton = computed(()=> { 
  const buscarnumero = arrayNuevo.value.find((numero) => numero === valor.value);
  if(buscarnumero === 0) return true;
  return buscarnumero ? true :false;
});
</script>

<template>
  <div class="container text-center mt-3">
    <h1> {{ saludo }} </h1> <br>
    <h2 :class="cambioColor"> {{ valor }}</h2><br>
    <button @click="incrementar" class="btn btn-success"> incrementar</button>
    <button @click="disminuir" class="btn btn-primary"> disminuir</button>
    <button @click="resert" class="btn btn-danger"> resetear </button>
    <button @click="add" :disabled="disableBoton" class="btn btn-info"> agregar</button>
    
    <ul class="list-group mt-4">
      <li v-for="(iten, index) in arrayNuevo" :key="index" class="list-group-item mt-1">
        {{ arrayNuevo[index] }}

      </li>
    </ul>

  </div>
</template>
<style>
.neutro {
  color: aqua;
}
.positive {
  color: rgb(244, 12, 252);
}
.negative {
  color: yellow;
}


</style>