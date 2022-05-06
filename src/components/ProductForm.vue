<template>
  <form 
  @submit.prevent="onSubmit"
  class="product-add">
    <label class="require" for="text">Наименование товара</label>
    <input v-model="name" type="text" name="name" placeholder="Введите наименование товара">
    
    <label for="description">Описание товара</label>
    <textarea v-model="description" name="description" placeholder="Введите описание товара"></textarea>
    
    <label class="require" for="img-link">Ссылка на изоображение товара</label>
    <input v-model="image" type="url" name="img-link" placeholder="Введите ссылку">
    
    <label class="require" for="price">Цена товара</label>
    <input v-model="price" type="text" name="price" placeholder="Введите цену">
    
    <input type="submit" class="btn-reset add-btn" value="Добавить товар">
  </form>

</template>

<script>
export default {
  data () {
    return {
      name: '',
      description: '',
      image: '',
      price: 0,
    }
  },
  methods: {
    onSubmit() {
      this.$emit('onSubmit', {
        id: Date.now(),
        name: this.name,
        description: this.description,
        image: this.image,
        price: this.price
      })
    }
  }
}
</script>

<style scoped>

  .product-add {
    flex: 0 0 332px;
    align-self: flex-start;
    width: 332px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    padding: 24px;
    margin-right: 16px;
    color: var(--text-gray);
    background-color: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
  }
  .product-add label {
    font-size: 10px;
    line-height: 13px;
    color: #49485E;
  }
  .product-add label > input, textarea {
    margin-top: 4px;
  }
  .product-add textarea {
    width: 100%;
    resize: none;
  }
  .product-add input,
  .product-add textarea {
    width: 100%;
    padding: 10px 16px;
    font-size: 12px;
    line-height: 15px;
    border: none;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
  }
  .require {
    position: relative;
  }
  .require::after {
    position: absolute;
    content: "";
    width: 4px;
    height: 4px;
    top: 0;
    background: #FF8484;
    border-radius: 4px;
  }
  .btn-reset {
    padding: 0;
    font-size: inherit;
    font-family: inherit;
    color: inherit;
    border: none;
    background: transparent;
    cursor: pointer;
  }
  .add-btn {
    display: block;
    margin-top: 24px;
    font-family: Inter;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    color: #B4B4B4;
    background: #EEEEEE;
    border-radius: 10px;
    transition: all .25s ease;
    -webkit-transition: all .25s ease;
  }
</style>