<template>
  
  <div id='mainBlockComponentLocalStorageApp'>


      <!-- <div>
        {{ titolo }}
      </div> -->

      <componente-globale />


  </div>



</template>




<script>


import componente from './components/componenteContenitoreGlobale.vue';

export default {

components:
{
  "componente-globale": componente,
},

  data()
 {
   return{
     titolo: "componente App"
   }
 }



}
</script>