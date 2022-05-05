<template>
  <div class="container">
    <product-form />
    <product-list />
  </div>

</template>

<script>
import ProductForm from '@/components/ProductForm.vue'
import ProductList from '@/components/ProductList.vue'
export default {
  name: 'App',
  components: {
    ProductForm,
    ProductList
  },

}
</script>

<style src="./assets/css/app.css"></style>
