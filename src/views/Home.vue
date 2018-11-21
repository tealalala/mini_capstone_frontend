<template>
  <div class="home">

    <!-- <ul>
      <li v-for="product in products">
        <p>id: {{ product.id }}</p>
        <p>name: {{ product.name }}</p>
        <p>price: {{ product.price }}</p>
        <p>description: {{ product.description }}</p>
        <p>is_discounted: {{ product.is_discounted }}</p>
      </li>
    </ul> -->

    <div class="container">
      <h1 align="center">{{ message }}</h1>

      <div class="row">
        <div class="col-sm-6" v-for="product in products">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">{{ product.name }}</h5>
              <p class="card-text"><p>${{ product.price }}</p>
              <p class="card-text"><p><img v-bind:src="product.images"></p>
              <p>description: {{ product.description }}</p>
              <p>stock status: {{ product.status }}</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style>
</style>

<script>
// var axios = require("axios");
import axios from 'axios'

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
