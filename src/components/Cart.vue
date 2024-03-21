<template>
    <div>
      <br>
        <h2>YOUR ORDER</h2>
        <div v-if="cart.length === 0" class="empty-cart">Your cart is empty.</div>
        <div v-else>
            <div class="cart-table-container">
                <table class="cart-table">
                    <thead>
                        <tr>
                            <th>Item</th>
                            <th>Price</th>
                            <th>Quantity</th>
                            <th>Total</th>
                            <th>Update Quantity</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(item, index) in cart" :key="index">
                            <td>{{ item.name }}</td>
                            <td>P {{ item.price }}</td>
                            <td>{{ item.quantity }} </td>
                            <td>P {{ item.price * item.quantity }}</td>
                            <td>
                                <button @click="addQuantity(item)">+</button>
                                <button @click="minusQuantity(item)">-</button>
                                <button @click="deleteItem(item)">Delete Order</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <p class="total-price">Total Amount: P {{ calculateTotalPrice() }}</p>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['cart'],
    methods: {
        addQuantity(item) {
            item.quantity++;
        },
        minusQuantity(item) {
            if (item.quantity > 1) {
                item.quantity--;
            }
        },
        deleteItem(item) {
            const index = this.cart.indexOf(item);
            if (index !== -1) {
                this.cart.splice(index, 1);
            }
        },
        calculateTotalPrice() {
            return this.cart.reduce((total, item) => total + (item.price * item.quantity), 0);
        }
    }
  };
  </script>
  
  <style scoped>
  .empty-cart {
      text-align: center;
      font-style: italic;
  }
  
  .custom-empty-message {
      color: #5a5858;
  }
  .cart-table-container {
    overflow-x: auto;
  }
  
  .cart-table {
    background-color: #464544e7;
    width: 100%;
    border-collapse: collapse;
  }
  
  .cart-table th, 
  .cart-table td {
    color: rgb(204, 200, 200);
    font-family: 'Times New Roman', serif;
    font-size: 15px;
    font-weight: bold;
    border: 1px solid rgb(10, 10, 10);
    padding: 8px;
    text-align: center;
  }
  
  .cart-table th {
    background-color: #252524cb;
  }
  
  .total-price {
    color: rgb(235, 146, 74);
    font-family: 'Courier New', Courier, monospace;
    font-size: 18px;
    font-weight: bold;
    text-align: right;
  }
  
  button {
    background-color: #d4511e;
    color: white;
    border: none;
    padding: 5px 10px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 12px;
    margin: 2px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #c58b64;
  }
  
  @media screen and (max-width: 768px) {
    .cart-table th,
    .cart-table td {
        font-size: 12px;
        padding: 5px;
    }
  }
  </style>
  