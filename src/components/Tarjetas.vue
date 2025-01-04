<template>
    <section class="bg-white overflow-hidden rounded-xl shadow-md flex w-[250px] mt-10 h-[250px]">
        <div class="w-1/6 h-full relative bg-black overflow-hidden">
            <div class="-rotate-90 absolute left-0 bottom-0 translate-y-10 origin-[0_0] w-[300px] pt-2 flex items-center justify-center">
                <p class="text-center text-2xl font-bold italic text-white max-w-full shadow-lg">{{ shortTitle }}</p>
            </div>
        </div>
        <div class="primera-vista w-5/6 flex flex-col">
            <div class="h-3/4 flex justify-center items-center p-4">
                <div :style="{ backgroundImage: `url(${Foto})` }" class="bg-cover bg-center bg-no-repeat rounded-md w-full h-full"></div>
            </div>
            <div class="h-1/4 flex justify-around items-center">
                <!-- Favorito and Compra components -->
                <div><Favorito /></div>
                <div class="text-black font-bold">{{ Precio }}</div>
                <div><Compra /></div>
            </div>
        </div>
        <div class="segunda-vista flex w-5/6 flex-col">
            <div class="h-3/4 flex justify-center items-center p-4">
                <div>{{ Rating }}</div>
            </div>
            <div class="h-1/4 flex justify-around items-center">
                <div><Favorito /></div>
                <a :href="Url" class="text-black font-bold cursor-pointer hover:text-blue-500">Ver Producto</a>
                <div><Compra /></div>
            </div>
        </div>
    </section>
    </template>
    
    <script setup>
    import { computed } from 'vue'
    import Compra from '../assets/compra.vue'
    import Favorito from '../assets/favorito.vue'
    
    const props = defineProps({
        Precio: String,
        Foto: String,
        Titulo: String,
        Rating: String,
        Url: String,
    })
    
    const getShortTitle = (titulo) => {
        const words = titulo.split(' ')
        if (words.length > 2) {
            return words.slice(0, 2).join(' ')
        }
        return titulo
    }
    

    const shortTitle = computed(() => getShortTitle(props.Titulo))
    </script>
    
    <style scoped>
    .segunda-vista {
        display: none;
    }
    
    .primera-vista:hover {
        display: none;
    }
    
    .primera-vista:hover + .segunda-vista {
        display: flex;
    }
    </style>