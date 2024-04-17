<template>
  <div class="pos-app">
    <product-list :products="productList" @add-to-cart="addToCart" />
    <order-summary :cart="cart" @remove-from-cart="removeFromCart" @checkout="checkout" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import OrderSummary from './components/OrderSummary.vue';



export default {
  components: {
    ProductList,
    OrderSummary,
  },
  data() {
    return {
      cart: [],
      productList: [
        { id: 1, name: 'Product A', price: 10.00 },
        { id: 2, name: 'Product B', price: 15.00 },
        { id: 3, name: 'Product C', price: 20.00 },
      ], // Replace with your actual product data
    };
  },
  // ... other methods (unchanged)
};
</script>

