<template>
  <li
    class="product-list__item card"
    @mouseenter="setRemoveVisibility(true)"
    @mouseleave="setRemoveVisibility(false)"
  >
    <div class="card__img">
      <img src="../assets/images/photo.jpg" :alt="product.name" />
    </div>
    <div class="card__text">
      <h2 class="card__title">{{ product.name }}</h2>
      <p class="card__description">{{ product.description }}</p>
      <span class="card__price">{{ formatPrice }}</span>
    </div>
    <transition name="fade">
     <button
      v-if="this.removeVisible"
      @click="removeProduct"
      class="remove-btn"></button>
    </transition>
  </li>
</template>

<script>
export default {
  name: 'ProductListItem',
  data() {
    return {
      removeVisible: false,
    };
  },
  props: {
    product: {
      type: Object,
      reqired: true,
    },
  },
  computed: {
    formatPrice() {
      return this.product.price
        .toString()
        .split('')
        .reverse()
        .map((char, i) => char + (i % 3 ? '' : ' '))
        .reverse()
        .join('');
    },
  },
  methods: {
    setRemoveVisibility(visible) {
      this.removeVisible = visible;
    },
     removeProduct() {
      this.$emit('removeProduct', this.product.id)
    },
  },
};
</script>

<style scoped>
.product-list__item {
  position: relative;
  flex: 1 1 332px;
  display: flex;
  flex-direction: column;
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
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
.remove-btn {
  position: absolute;
  top: -10px;
  right: -10px;
  width: 36px;
  height: 36px;
  background: url('@/assets/images/del.svg');
  border: none;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
