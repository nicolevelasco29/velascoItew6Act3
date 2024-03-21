<template>
  <div>
    <ProductList :products="products" @add-to-cart="addToCart" />
    <Cart :cart="cart" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import Cart from './components/Cart.vue';

export default {
  components: {
    ProductList,
    Cart
  },
  data() {
    return {
      products: [
        { id: 1, name: 'TSHIRT', price: 150 },
        { id: 2, name: 'DRESS', price: 500 },
        { id: 3, name: 'POLO', price: 200 },
        { id: 4, name: 'JACKET', price: 350 },
        { id: 5, name: 'PANTS', price: 500 },

      ],
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      const itemInCart = this.cart.find(item => item.id === product.id);
      if (itemInCart) {
        itemInCart.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    }
  }
};
</script>
