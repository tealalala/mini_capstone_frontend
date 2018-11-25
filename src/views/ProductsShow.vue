<template>
  <div class="productsShow">

    <div class="container">
      <h1 align="center">{{ message }}</h1>

      <div class="row">
        <!-- <div class="col-sm-6" v-for="product in products"> -->
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
        <!-- </div> -->
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      message: "Product Show 1",
      product: {}
    };
  },
  created: function() {
    console.log(this.$route.params.id);
    axios.get('http://localhost:3000/api/products/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.product = response.data;
    })
  },
  methods: {},
  computed: {}
};
</script>
