<template>
      <ul class="product-list">
        <product-list-item />
      </ul>
</template>

<script>
import ProductListItem from '@/components/ProductListItem.vue'

export default {
  components: { ProductListItem },
  
}
</script>

<style scoped>
  .product-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    gap: 16px;
  }
</style>