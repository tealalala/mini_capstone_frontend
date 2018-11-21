<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <ul>
      <li v-for="product in products">
        <p>id: {{ product.id }}</p>
        <p>name: {{ product.name }}</p>
        <p>price: {{ product.price }}</p>
        <p>description: {{ product.description }}</p>
        <p>is_discounted: {{ product.is_discounted }}</p>
      </li>
    </ul>

  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      message: "Mini Capstone - Products Index",
      products: []
    };
  },
  created: function() {
    axios.get('http://localhost:3000/api/products').then(function(response) {
      console.log(response.data);
      this.products = response.data;
    }.bind(this))
  },
  methods: {},
  computed: {}
};
</script>
