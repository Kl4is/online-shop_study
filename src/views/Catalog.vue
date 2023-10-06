<template>
 <div class="products-list">

  
  <v-row no-gutters>
      <v-col
        v-for="product in store.products"
        :key="product.id"
        @click="goToProductPage(product.id)" 
        cols="12"
        sm="4"
      >
      
        <product-item
        class="products"
          :product-data="product"
          @item-clicked="goToProductPage"
        />
      </v-col>
    </v-row>

      

 </div>
</template>

<script>
  import { defineComponent } from 'vue';
  import ProductItem from '../components/ProductItem.vue';
  export default defineComponent({
    name:'CatalogView',
    components:{
      ProductItem
    }
  })
  import { createVuetify } from 'vuetify'
import { aliases, fa } from 'vuetify/iconsets/fa'
import { mdi } from 'vuetify/iconsets/mdi'
    createVuetify({
  icons: {
    defaultSet: 'fa',
    aliases,
    sets: {
      fa,
      mdi,
    },
  },
})
</script>

<script setup>
  import { onMounted, ref } from 'vue';
  import {productsStore} from '../stores/products'
  import { useRouter} from "vue-router"

  const store = productsStore()
  const router = useRouter()
  const search =ref('')

  const goToProductPage = (id) => {
    router.push({name: 'ProductView', params: {id}})
  }


  onMounted(async() => {
    await store.fetchProductsFromDB()
  })
</script>

<style scoped>

</style>