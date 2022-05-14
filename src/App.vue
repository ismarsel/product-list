<template>
    <div class="section-header container">
      <h1 class="section-title">Добавление товара</h1>
      <select class="select" name="sort-product-list" disabled="disabled">
        <option value="default">По умолчанию</option>
      </select>
      <sort-select
        :options="sortOptions"
        :default="sortOptions[0]"
        @changeValue="sort($event)"/>
    </div>
  <div class="container">
    <product-form @onSubmit="handleSubmit" />
    <product-list 
    :products="products"
     @removeProduct="removeProduct($event)" />
  </div>
</template>

<script>
import ProductForm from '@/components/ProductForm.vue';
import ProductList from '@/components/ProductList.vue';
import SortSelect from '@/components/UI/SortSelect.vue'
export default {
  name: 'App',
  components: { ProductForm, ProductList, SortSelect },
  data() {
    return {
      products: [
        {
          id: 0,
          image: '/photo.jpg',
          name: 'яНаименование товара',
          description:
            'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк.',
          price: 10000,
        },
                {
          id: 2,
          image: '/photo.jpg',
          name: 'аНаименование товара',
          description:
            'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк.',
          price: 14000,
        },
        {
          id: 1,
          image: '/photo.jpg',
          name: 'Наименование товара',
          description:
            'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк.',
          price: 12000,
        },
      ],
      sortOptions: [
        {
          value: 'byName',
          text: 'По Имени'
        },
        {
          value: 'byPriceMax',
          text: 'По возрастанию цены'
        },
        {
          value: 'byPriceMin',
          text: 'По убыванию цены'
        }
      ],
    };
  },
  methods: {
    handleSubmit(product) {
      this.products.push(product);
    },
    removeProduct (productId) {
      this.products = this.products.filter(p => p.id !== productId)
    },
    sort (sortOption) {
        if (sortOption === 'byName') {
          this.products = this.products.sort((firstEl, secondEl) => { return firstEl.name > secondEl.name ? 1 : -1 })
        } else if (sortOption === 'byPriceMax') {
          this.products = this.products.sort((firstEl, secondEl) => { return firstEl.price > secondEl.price ? 1 : -1 })
        } else if (sortOption === 'byPriceMin') {
          this.products = this.products.sort((firstEl, secondEl) => { return firstEl.price < secondEl.price ? 1 : -1 })
        }
      }
  },
};
</script>

<style src="./assets/css/app.css"></style>
