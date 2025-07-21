
<script setup>
import { ref } from 'vue';
import Modal from '../detalles/modal.vue';

const props = defineProps({
  title: String,
  description: String,
  precio: String,
  img: String,
});

const showModal = ref(false);

function consoleFuction() {
  showModal.value = true;
}

function close() {
  showModal.value = false;
  }
</script>
<template>
<div class="h-full w-full rounded-xl bg-[#f6f6f6] shadow-xl">
  <!-- Imagen -->
  <div class="bg-[#f6f6f6] border rounded-t-xl h-3/5 overflow-hidden flex items-center justify-center">
    <img 
      class="object-cover h-full w-full"
      src="img/productos/pollo.jpg"
      alt=""
    >
  </div>

  <!-- Contenido inferior con distribución fija -->
  <div class="flex flex-col bg-white h-2/5 border rounded-b-xl p-4">
    <p class="font-bold text-lg mb-2 truncate">{{title}}</p>

    <!-- Descripción con scroll si es muy larga -->
    <p class="min-h-[4rem] max-h-[4.5rem] overflow-y-auto text-sm mb-2">
      {{description}}

    </p>

    <p class="text-[#1abc9c] font-bold text-2xl mb-4">
    <span>Precio</span> {{precio}}
    </p>

    <!-- Botón anclado abajo sin cambiar de tamaño -->
    <div class="mt-auto">
      <button
        @click="consoleFuction"
        class="w-full bg-[#1abc9c] text-white font-bold py-2 rounded-xl hover:bg-[#16a085] transition duration-300">
        Ver detalles
      </button>
    </div>
  </div>
</div>



<Modal
  :show="showModal"
  :title="title"
  :description="description"
  :precio="precio"
  @close="close"
/>
</template>

