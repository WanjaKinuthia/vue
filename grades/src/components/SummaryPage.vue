<template>
  <div class="pos-app">
    <product-list @add-to-cart="addToCart" />
    <order-summary :cart="cart" @remove-from-cart="removeFromCart" @checkout="checkout" />
  </div>
</template>

<script>
import ProductList from './ProductList.vue';
import OrderSummary from './OrderSummary.vue';

export default {
  components: {
    ProductList,
    OrderSummary,
    cartView,
  },
  data() {
    return {
      cart: [], // Array of selected products
    };
  },
  methods: {
    addToCart(product) {
      const existingItem = this.cart.find((item) => item.id === product.id);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        product.quantity = 1;
        this.cart.push(product);
      }
    },
    removeFromCart(product) {
      const index = this.cart.findIndex((item) => item.id === product.id);
      if (index > -1) {
        this.cart.splice(index, 1);
      }
    },
    checkout() {
      // Implement checkout logic (e.g., display payment modal)
      alert('Checkout initiated!');
    },
  },
};
</script>

<style scoped>
.pos-app {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
}
</style>
