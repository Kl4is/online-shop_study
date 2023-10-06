<template>
  <header>
    <v-toolbar title="All market" >
      <v-btn 
      color="brown"
      variant="outlined"
      @click="router.push({ name: 'CartView' })"
      >
        Item in Cart: {{ store.cart.length }}
      </v-btn>
    </v-toolbar>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<script setup>
import {useRouter} from 'vue-router'
import { productsStore } from './stores/products';
//import router from './router';

const router = useRouter()
const store = productsStore()
</script>



<style scoped>

  .cart-items{
    text-align: end;
    padding: 16px;
    font-weight: bold;
    font-size: 14px;
    cursor: pointer;
  }
  
</style>
