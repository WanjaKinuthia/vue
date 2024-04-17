<template>
  <div v-if="cart.length > 0">
    <h3>Order Summary</h3>
    <ul>
      <li v-for="item in cart" :key="item.id">
        {{ item.name }} (x{{ item.quantity }}) - KES {{ item.price * item.quantity }}
        <button @click="$emit('remove-from-cart', item)">Remove</button>
      </li>
    </ul>
    <button @click="$emit('checkout')">Checkout (KES {{ calculateTotal }})</button>
  </div>
  <div v-else>
    <p>No items in cart.</p>
  </div>
</template>

<script>
export default {
  props: {
    cart: Array,
  },
  computed: {
    calculateTotal() {
      return this.cart.reduce((acc, item) => acc + (item.price * item.quantity), 0);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
li {
  margin-bottom: 10px;
}
</style>
