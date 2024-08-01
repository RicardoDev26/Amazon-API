<template>
  <section class="flex flex-col gap-9 justify-center items-center">
    <div class="flex flex-col gap-4">
      <div class="text-4xl lg:text-6xl text-black font-black">AMAZONONE</div>
      <div class="relative flex justify-center">
        <input
          v-model="BusquedaReactiva"
          type="text"
          @keyup.enter="Busqueda"
          placeholder="Buscar Producto"
          class="h-[50px] w-[250px] lg:w-[450px] rounded-full outline-none border-solid border-black border-[2px] p-3 pl-12 pr-4"
        />
        <div
          @click="Busqueda"
          class="absolute inset-y-0 left-0 flex items-center pl-3 cursor-pointer"
        >
          <search class="w-6 h-6 text-gray-500"/>
        </div>
      </div>
    </div>
    <div class="flex flex-wrap justify-center gap-32 bg-gray-500">
      <div v-for="producto in productos" :key="producto.product_url">
        <Tarjeta
          :Precio="producto.product_price"
          :Titulo="producto.product_title"
          :Foto="producto.product_photo"
          :Rating="producto.product_star_rating"
          :Url="producto.product_url"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import search from '../src/assets/searchLogo.vue';
import Tarjeta from './components/Tarjetas.vue';
import { ref } from 'vue';

const BusquedaReactiva = ref('');

const options = {
  method: 'GET',
  headers: {
    'x-rapidapi-key': '0aed54e031msh4fdc0fc329eb309p1cdb43jsn0e00643695ef',
    'x-rapidapi-host': 'real-time-amazon-data.p.rapidapi.com',
    'Content-Type': 'application/json',
  },
};
const productos = ref([]);

const Busqueda = async () => {
  try {
    const response = await fetch(`https://real-time-amazon-data.p.rapidapi.com/search?query=${BusquedaReactiva.value}&page=1&country=US&sort_by=RELEVANCE&product_condition=ALL`, options);
    const result = await response.json();
    productos.value = result.data.products;
    console.log(result.data.products);
  } catch (error) {
    console.error(error);
  }
};
</script>

<style scoped>
/* body {
  background-color: #6b7280;
} */
</style>
