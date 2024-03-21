<template>
    <div class="shop-name">
      <p>Nicole's Clothing Shop</p>
      </div>
      <br>
      <ul class="product-list">
        <li v-for="product in products" :key="product.id" class="product-item">
          <div class="product-info">
            <p class="product-name">{{ product.name }}</p>
            <p class="product-price">Price: P{{ product.price }}</p>
          </div>
          <button @click="addToCart(product)" class="add-to-cart-btn">Add to Cart</button>
        </li>
      </ul>
  </template>
  
  <script>
  export default {
    props: ['products'],
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      }
    }
  };
  </script>
  
  <style scoped>
  .shop-name {
    color: rgb(190, 136, 100);
    font-size: 25px;
    font-family: 'Times New Roman', serif;
    font-weight: bold;
    text-align: center;
  }
  .product-list {
    color: rgb(179, 170, 170);
    list-style: none;
    padding: 0;
  }
  
  .product-item {
    display: flex;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .product-info {
    flex: 1;
    display: flex;
    align-items: left;
  }
  
  .product-name {
    font-weight: bold;
    margin-right: 10px;
  }
  
  .product-price {
    color: #5a5858;
  }
  
  .add-to-cart-btn {
    background-color: #d4511e;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
  }
  button:hover {
  background-color: #c58b64;
}
  </style>