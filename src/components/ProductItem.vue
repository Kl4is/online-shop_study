<template>
  <v-sheet class="ma-2 pa-2">
          <v-card
          class="product"
          

      >
        <v-img
            :src="props.productData.thumbnail"
            height="200px"
            cover
        />
        
        <v-card-title>
           {{props.productData.brand}}
        </v-card-title>

        <v-card-subtitle>
          $ {{props.productData.price}}
        </v-card-subtitle>

        <v-card-text>
          {{ props.productData.description }}
        </v-card-text>        

        <v-card-actions>
          <v-btn class="btn_add" variant="outline" @click="goToProductPage(props.productData.id)">
            Add to cart
          </v-btn>
        </v-card-actions>
      </v-card>
        </v-sheet>
</template>

<script>
import {defineComponent} from 'vue';
export default defineComponent({
  name: 'ProductItem',
})
</script>

<script setup>
  import {defineProps, defineEmits} from 'vue'
  const props = defineProps({
    productData: {
      type: Object,
      requeired: true,
    }
  })

  const emit = defineEmits(['item-clicked'])

  const goToProductPage = (productId) => {
    emit ('item-clicked', productId)
  }
</script>

<style >
.btn_add{
  border: 3px solid aqua;
}
</style>