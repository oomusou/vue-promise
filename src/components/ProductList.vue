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
  async mounted() {
    try {
      const response = await productApi.fetchProducts();
      this.products = response.data;
    } catch (err) {
      console.log(err);
    } finally {
      console.log('finally');
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
