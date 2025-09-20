<script setup>
import { defineProps, defineEmits, onMounted, watch,ref} from 'vue';
import dataProducts from '../../data/products.json';
const props = defineProps({
  show: Boolean,
  title: String,
  idProduct: Number,
});

const product = ref({});

function searchProduct(){
  product.value  = dataProducts.find(product=> product.id === props.idProduct);
  
}

watch(() => props.show, (show) => {
  if (show) {
    searchProduct();
  }
});

const emit = defineEmits(['close']);
function close() {
  emit('close');
};
</script>

<template>

  <div v-if="show" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50"
    @click.self="close">
    <div
      class="bg-white p-6 m-4 rounded-lg relative flex flex-col justify-between w-[80vw] max-w-[80vw] md:w-[80vw] md:max-w-[80vw] lg:w-[60vw] lg:max-w-[60vw] xl:w-[50vw] xl:max-w-[50vw]">
      <h2 class="text-2xl font-bold mb-2">{{ product.nombre }}</h2>
      <button @click="close" class="absolute top-2 right-2 text-gray-500 hover:text-black">
        ✖
      </button>
      <div class="flex-1 flex flex-col justify-center items-center">
        <div class="w-full">
         <h5 class="text-xl font-bold mb-2">Descripcion</h5>
          <p class="text-sm mb-2">{{ product.descripcion }}</p>
        </div>
      </div>
      <div>
        <hr class="m-4">
        <h5 class="text-xl font-bold mb-2 ">Precentacion del producto</h5>
        <div class="grid grid-cols-2 gap-2" >
          
          <div 
           v-for = "[clave, valor] in Object.entries(product.detalles) " :key = clave
          class="w-full border bg-slate-100  rounded-lg p-2">
            <p class="font-bold">{{clave  }}</p>
            <p class="font-normal text-gray-500">{{valor}}</p>
          </div>
          <!-- <div class="w-full border bg-slate-100  rounded-lg p-2">
            <p class="font-bold ">Precentación</p>
            <p class="font-normal text-gray-500">Pieza grande tender</p>
          </div>
          <div class="w-full border bg-slate-100  rounded-lg p-2">
            <p class="font-bold ">Peso por bolsa</p>
            <p class="font-normal text-gray-500">10 libras</p>
          </div>
          <div class="w-full border bg-slate-100  rounded-lg p-2">
            <p class="font-bold ">Peso por bolsa</p>
            <p class="font-normal text-gray-500">10 libras</p>
          </div> -->
        </div>
        <hr class="m-4">
        <!-- <div>
          <h5 class="text-xl font-bold mb-2">Caracteristicas del producto</h5>
          <div class="flex items-center gap-2 mb-2">
             <div class="rounded-full h-8 w-8 bg-red-300 flex items-center justify-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
              </svg>
            </div>
            <p>Cuarto trasero de pollo premium, pieza grande tender</p>
          </div>
          <div class="flex items-center gap-2 mb-2">
             <div class="rounded-full h-8 w-8 bg-red-300 flex items-center justify-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
              </svg>
            </div>
            <p>Cuarto trasero de pollo premium, pieza grande tender</p>
          </div>
          <div class="flex items-center gap-2 mb-2">
            <div class="rounded-full h-8 w-8 bg-red-300 flex items-center justify-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
              </svg>
            </div>
            <p>Cuarto trasero de pollo premium, pieza grande tender</p>
          </div>
        </div> -->
      </div>
    </div>
  </div>


</template>
