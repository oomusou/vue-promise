<template>
  <div id="ProductList">
    <table border="1">
      <tr v-for="(product, index) in products" :key="index">
        <td width="150">{{ product.title }}</td>
        <td>{{ product.price }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import productApi from '../api/productApi';

export default {
  name: 'ProductList',
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    const response = res =>
      this.products = res.data;

    const error = e =>
      console.log(e);

    const done = () =>
      console.log('finally');

    productApi
      .fetchProducts()
      .then(response)
      .catch(error)
      .finally(done);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
