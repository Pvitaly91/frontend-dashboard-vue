
<template>
    <div class=" flex items-center justify-between mb-3">
        <h1 class="text-3xl font-semibold">Products</h1>
        <button type="submit"
            @click ="showProductModal"
            class="py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
            >
            Add new Product
        </button>

    </div>
   <ProductModal v-model="showModal" :product="productModel" @close="onModalClose"></ProductModal>
    <ProductsTable @clickEdit="editProduct"></ProductsTable>
</template>

<script setup>

import { ref } from "vue";
import ProductModal from "./ProductModal.vue";
import ProductsTable from "./ProductsTable.vue";
import store from "../../store";

const DEFAULT_PRODUCT = {
  id: '',
  title: '',
  description: '',
  image: '',
  price: ''
};


const showModal = ref(false);
const productModel = ref({DEFAULT_PRODUCT});

function showProductModal(){
  showModal.value = true;
}

function editProduct(p) {
  
  store.dispatch('getProduct', p.id)
    .then(({data}) => {
      productModel.value = data
      showProductModal();
      

    })
}
function  onModalClose(){
  productModel.value = {DEFAULT_PRODUCT};
}
</script>