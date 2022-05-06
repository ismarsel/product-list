<template>
  <div class="container">
    <product-form 
    @onSubmit="handleSubmit"/>
    <product-list 
    :products="this.products"/>
  </div>

</template>

<script>
import ProductForm from '@/components/ProductForm.vue'
import ProductList from '@/components/ProductList.vue'
export default {
  name: 'App',
  components: { ProductForm, ProductList },
  data () { 
    return {
      products: [
        {
          id: 0,
          image: '/photo.jpg',
          name: 'Наименование товара',
          description: 'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк.',
          price: 10000
        },
      ]
    }
  },
  methods: {
    handleSubmit(product) {
      this.products.push(product)
    },
  }
}
</script>

<style src="./assets/css/app.css"></style>
