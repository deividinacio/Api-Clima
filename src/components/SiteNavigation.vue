<template>
    <header class="sticky top-0 bg-weather-primary shadow-lg">
        <nav class="container flex-col sm:flex-row items-center gap-4 text-white py-6">
            <RouterLink :to="{name: 'home'}">
                <div class="flex item-center gap-3">    
                    <p class="text-2xl">Local do Clima</p>
                </div>
            </RouterLink>
            <div class="flex gap-3 flex-1 justify-end">
               <!-- <i class="fa-solid fa-circle-info text-xl hover:text-weather-secondary duration-150 cursor-pointer"></i> -->
              <!-- <i class="fa-solid fa-plus text-xl hover:text-weather-secondary duration-150 cursor-pointer"></i> -->
            </div>
            <!--
            <BaseModal  >
            <h1 class="text-black">Modal</h1>
            <p class="text-black">TESTE CONTEÚDO DA MODAL</p>
            </BaseModal>
            -->
        </nav>
    </header>
</template>

<script setup>
    import { RouterLink } from 'vue-router';
    
  
    /*
    const alternarModal = () =>{
        ativarModal.value = !ativarModal.value;
    };
    */
    
</script>

