<template>
  <div class ="intro"> 
  <div class="product">
    <div class="product-image">
      <img :src="selectedProduct.thumbnail" alt="">
    </div>
    <div class="product-details">
      <p>Brand: {{ selectedProduct.brand }}</p>
      <p>Description: {{ selectedProduct.description }}</p>
      <h2>Price: ${{ selectedProduct.price }}</h2>
      <v-btn @click="addToCart" variant="elevated" color="success">Add to cart</v-btn>
      <v-btn 
        @click="router.push({name:'Catalog'})" 
        variant="elevated" 
        color="grey-darken-4"
      >
        Back to catalog
    </v-btn>
    </div>
  </div>
</div>
</template>

<script>
  import {defineComponent ,computed} from 'vue';
  export default defineComponent({
    name:'ProductDetails'
  })
</script>

<script setup>
  import {computed} from 'vue';
  import { productsStore } from '../stores/products';
  import {useRoute, useRouter} from 'vue-router'

  const store = productsStore()
  const route = useRoute()
  const router = useRouter()

  const selectedProduct = computed(() =>{
    return store.products.find((item) => item.id === Number(route.params.id))
  })

  const addToCart = () => {
    store.addToCart(selectedProduct.value)
    router.push({name:'CartView'})
  }
</script>

<style scoped>

  .product{
    display: flex;
    margin-top: 50px;
  }
  .product-image{
    margin-right: 24px;
  }
  .button-back{
    display: flex;
    border-radius: 20px;
    background-color:orange;
  }
</style>