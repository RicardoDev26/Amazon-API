<template>
<section class="bg-white overflow-hidden rounded-xl shadow-md  flex w-[250px] h-[250px]">
    <div class="w-1/6 h-full relative bg-black overflow-hidden">
        <div class="-rotate-90 absolute left-0 bottom-0 translate-y-10 origin-[0_0] w-[300px] pt-2 ">
            <p class="text-center text-xl font-bold italic text-white max-w-full">{{ props.Titulo }}</p>
        </div>
    </div>
    <div class="primera-vista w-5/6 flex flex-col">
        <div class="h-3/4 flex justify-center items-center p-4">
            <div :style="{ backgroundImage: `url(${props.Foto})` }" class="bg-cover bg-center bg-no-repeat rounded-md w-full h-full"></div>

        </div>
        <div class="h-1/4 flex justify-around items-center">
            <div><Favorito /></div>
            <div class="text-black font-bold">{{ props.Precio }}</div>
            <div><Compra /></div>
        </div>
    </div>
    <div class="segunda-vista flex w-5/6 flex-col">
        <div class="h-3/4 flex justify-center items-center p-4">
            <div>{{ props.rating }}</div>
        </div>
        <div class="h-1/4 flex justify-around items-center">
            <div><Favorito /></div>
            <a :href="props.Url" class="text-black font-bold cursor-pointer hover:text-blue-500">Ver Producto</a>
            <div><Compra /></div>
        </div>
    </div>
</section>
    
</template>
<script setup>
import Compra from '../assets/compra.vue'
import Favorito from '../assets/favorito.vue'
import start from '../assets/start.vue'


const props = defineProps( {
    Precio: String,
    Foto: String,
    Titulo: String,
    Rating: String,
    Url: String,
})

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