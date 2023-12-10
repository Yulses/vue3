//Logica
<script setup>
  import { pushScopeId, ref } from 'vue'
  let contador= ref(0);
  let registroDelContador= ref([])

  const cambiarColor= function(){
   if(contador.value==0){
    return 'clases_zero';
   }
   else if(contador.value>0){
      return 'clases_positivo'
   }
   else if(contador.value<0){
    return 'clases_negativo'
   }
   else{
    return 'clases_porDefecto'
   }
  }
  const agregarContador=function(){
    
    if(registroDelContador.value.indexOf(contador.value)==-1){
      registroDelContador.value.push(contador.value);
    }

  }
  const bloquearBoton= function(){
    if(registroDelContador.value.indexOf(contador.value)==-1){
      return '';
    }
    else{
      return 'place_order'
    }
  }

</script>
//Estryctura
<template>
  <div class="container mx-auto p-2" >
    
    <h1> Hola mundo </h1>
  <p v-bind:class="cambiarColor()">Contador: {{ contador }}</p>
  <div class="btn-group">
    <button class="btn btn-success " @click="contador++">Incrementar</button>
  
  <button class="btn btn-danger" @click="contador--">Decrementar</button>

  <button class="btn btn-primary" @click="contador=0">Resetear</button>

  <button class="btn btn-warning" @click="agregarContador" :class="bloquearBoton()">Agregar</button>
</div>
  <p><ul class="list-group">
    <li  class="list-group-item list-group-item-primary text-center" v-for="lista in registroDelContador">
        {{ lista }}
      
    </li>
  </ul></p>

</div>

</template>
//Estilos
<style>

  .clases_zero{color:blue}

  .clases_positivo{color:greenyellow}

  .clases_negativo{color:red}

  .clases_porDefecto{color:white}

  .place_order
    {
        cursor: not-allowed;
        background-color: rgb(229, 229, 229) !important;
        pointer-events:none;
        color:gray;
    }

</style>