<template>
  <ul class="product-list">
     <transition-group name="list" tag="p">
      <product-list-item
        v-for="product in products"
        :key="product.id"
        :product="product"
        @removeProduct="removeProduct($event)"
      />
     </transition-group>
  </ul>
</template>

<script>
import ProductListItem from '@/components/ProductListItem.vue';

export default {
  name: 'ProductList',
  components: { ProductListItem },
  props: {
    products: {
      type: Array,
      reqired: true,
    },
  },
  methods: {
    removeProduct(productId) {
      this.$emit('removeProduct', productId)
    }
  }
};
</script>

<style scoped>
.product-list {
  align-self: flex-start;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 16px;
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all .3s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all .3s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.product-list p {
  align-self: flex-start;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 16px;
}
</style>
