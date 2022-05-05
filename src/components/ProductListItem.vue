<template>
  <li class="product-list__item card">
    <div class="card__img">
      <img src="" alt="Фотоаппарат">
    </div>
    <div class="card__text">
      <h2 class="card__title">Наименование товара</h2>
      <p class="card__description">
        Довольно-таки интересное описание товара в несколько строк.
        Довольно-таки интересное описание товара в несколько строк.
      </p>
      <span class="card__price">10000 руб.</span>
    </div>
  </li>
</template>

<script>
export default {
}
</script>

<style scoped>
  .product-list__item {
    flex: 1 1 332px;
    display: flex;
    flex-direction: column;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
  }
  .card__img {
    width: 100%;
    height: 200px;
  }
  .card__img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .card__text {
    padding: 16px;
  }
  .card__title {
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
  }
  .card__description {
    padding: 1em 0 2em;
    line-height: 20px;
  }
  .card__price {
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
  }

</style>