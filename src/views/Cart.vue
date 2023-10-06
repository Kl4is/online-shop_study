<template>
  <div class="btn_item">
   <button class="btn_card" @click="router.push({name:'Catalog'})">Back in catalog</button>
  </div>
   <div v-if="!store.cart.length" style="text-align: center;">
    <h1>Empty Cart...</h1>
  </div>

  <div class="cart-items" v-else>
    <div 
      class="cart-item"
      v-for="item in store.cart"
      :key="item.id"
    >

      <div class="item-details">
        <img :src="item.thumbnail" alt="">
        <span>Brand: {{ item.brand }}</span>
        <span>Category: {{ item.category }}</span>
        <span>Price: ${{ item.price }}</span>
        <button class="btn_remove" @click="removeFromCart(item.id)">Remove</button>
      </div>
    </div>
  </div>
</template>

<script>
  import { defineComponent } from 'vue';
  export default defineComponent({
    name:'CartView'
  })
</script>

<script setup>
  import {useRouter} from 'vue-router'
  import { productsStore } from '../stores/products';

  const router = useRouter()
  const store = productsStore()

  const removeFromCart= (id) =>{
    store.removeFromCart(id)
  }

</script>

<style scoped>
  .item-details{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 32px;
    box-shadow: 0px 0px 17px 6px #e7e7e7;
    border-radius: 8px;
  }
  .item-details img{
    width: 20%;
    border-radius: 8px;
  }
  .btn_item{
    position: relative;
    margin-bottom: 55px;
  }
  .btn_card{
    border: 1px solid brown;
    border-radius: 5px;
    color: brown;
    padding: 5px;
    position: absolute;
    right: 0;
    
  }
  .btn_remove{
    margin-right: 15px;
    padding: 5px;
    transition: transform 0.2s linear;
  }
  .btn_remove:hover {
    border: 1px solid black;
    border-radius: 5px;
  }
  
</style>