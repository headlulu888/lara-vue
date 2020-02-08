<template>
  <div class="product">
    <h1>This is an products page</h1>
    <table>
      <tr>
        <td>Id</td>
        <td>Name</td>
        <td>Description</td>
      </tr>
      <tr v-for="product in products">
        <td>{{product.id}}</td>
        <td>{{product.name}}</td>
        <td>{{product.desc}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Products',
    data: () => {
      return {
        products: [
          {
            name: 'john',
            desc: 'test123'
          },
          {
            name: 'ivar',
            desc: 'test321'
          }
        ],
      }
    },
    mounted() {
      console.log('Products is mounted !');
      axios.get('http://127.0.0.1:8000/api/products').then(response => {
        this.products = response.data
      })
    }
  }
</script>

<style>
  table {
    width: 100%;
  }
  table tr, table td {
    border: 1px solid black
  }
</style>