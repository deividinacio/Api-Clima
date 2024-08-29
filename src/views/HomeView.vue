<script setup>
</script>

<template>
  <main class="container text-white">
    <div class="pt-4 mb-8 relative">
      <input type="text" 
      v-model="queryPesquisa"
      @input="getResultadoPesquisa"
      placeholder="Escolha uma cidade" 
      class="py-2 px-1 w-full bg-transparent boder-b focus:border-weather-secondary focus:outline-none focus:shadow-[0px_1px_0_0_#004E71]"/>
    
    
    </div>
    
  </main>
</template>

<script setup>
 import{ref} from 'vue';
 import axios from 'axios';

 const queryPesquisa = ref("");
 const queryTimeout = ref(null);
 const keyApi = "ca7ac432";
 const apiResultadoPesquisa= ref(null);



 const getResultadoPesquisa = () => {
    clearTimeout(queryTimeout.value);
  queryTimeout.value = setTimeout(async () => {
      if (queryPesquisa.value !=="") {
        const resultado = await axios.get(`https://api.hgbrasil.com/weather?key=${keyApi}&city_name=${queryPesquisa.value},SP`);
        apiResultadoPesquisa.value = resultado.data.features;
        console.log(apiResultadoPesquisa.value);  
        return;
      }
      apiResultadoPesquisa.value = null;
    }, 300);
 };
</script>
