<script setup>
</script>

<template>
  <main class="container text-white">

    <div class="mt-5 mb-5 ">
      <input type="text" 
      v-model="queryPesquisa"
      @input="getResultadoPesquisa"
      placeholder="Escolha uma cidade" 
      class="py-2 px-1 w-full bg-transparent boder-b focus:border-weather-secondary focus:outline-none focus:shadow-[0px_1px_0_0_#004E71]"/>
    
    </div>
    <div class="-mt-2 p-2 lg:mt-0 lg:w-full lg:max-w-md lg:flex-shrink-0 ">
          <div class="rounded-3xl
           bg-weather-secondary 
           py-10  ring-1 ring-inset h-100 relative">
            <div v-if="apiResultadoPesquisa" class="mx-auto max-w-xs px-8">
              <div class="text-center ">
                 <p>
                   <span> <i class="fa-solid fa-location-dot mr-5"></i></span>
                   <span class=" text-3xl font-semibold text-white"> {{apiResultadoPesquisa.data[0].city_name}} </span>
                   
                 </p>
                 <p>
                   <span class="text-xl  text-white">{{apiResultadoPesquisa.data[0].state_code}}</span>
                   <span class="text-xl  text-white ml-9">{{apiResultadoPesquisa.data[0].country_code}}</span>
                 </p>
                  
                 <p class="mt-8">
                    <span class="text-8xl font-bold  text-white">{{Math.round(apiResultadoPesquisa.data[0].temp)}}º</span>
                    <span class="text-6xl">C</span>
                     <span class="flex gap-3 flex-1 justify-center">
                      <img class="object-right " v-bind:src= "caminhoIcon + `${apiResultadoPesquisa.data[0].weather.icon}` + '.png'">
                     </span>
                  </p>
                   
              <p class="mt-6 text-xs leading-5 text-white">
                <sup class="text-xl">{{ apiResultadoPesquisa.data[0].weather.description }}</sup>
              </p>
              <p class="mt-6 text-xs leading-5 text-white">
                <span>Nascer Sol: </span>
                <span class="mr-9">{{ apiResultadoPesquisa.data[0].sunrise}}</span>
                <span>Por do Sol: </span>
                <span>{{ apiResultadoPesquisa.data[0].sunset }}</span>
              </p>
              </div>
            </div>
          </div>
        </div>
  </main>
</template>

<script setup>
 import{ref} from 'vue';
 import axios from 'axios';

 const queryPesquisa = ref(""); 
 const queryTimeout = ref(null);
 const keyApi = "5028c11c3dc64c41a27c455513cfa505";
 const apiResultadoPesquisa = ref(null);
 const caminhoIcon = "https://cdn.weatherbit.io/static/img/icons/"; 

const getResultadoPesquisa = () => {
  clearTimeout(queryTimeout.value);
  queryTimeout.value = setTimeout(async () => {
    if(queryPesquisa.value !== "" ) {
      const resultado = await axios.get(`http://api.weatherbit.io/v2.0/current?&city=${queryPesquisa.value}&country=US&key=${keyApi}&lang=pt`
      );
      apiResultadoPesquisa.value = resultado.data;
    //  console.log(apiResultadoPesquisa.value);
      return ;
    }
  apiResultadoPesquisa.value = null;
  }, 300);
};

</script>
