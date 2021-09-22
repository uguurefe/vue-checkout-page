<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="container">
      <Navbar />
      <div class="row">
        <div class="col-12 col-md-8">
          <CartItemList :list="list" />
        </div>
        <div class="col-12 col-md-4">
          <CartSummary :summary="cartSummary" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import CartItemList from './components/CartItemList'
import CartSummary from './components/CartSummary'
export default {
  name: 'App',
  components: {
    // HelloWorld
    Navbar,
    CartItemList,
    CartSummary
  },
  data(){
    return{
      list: [],
      cartSummary: {}
    }
  },
  methods:{
    async getData(){
      const response = await this.axios.get("http://localhost:3004/cart")
      .catch( (error) => alert('Error ', error.message));
      console.log(response.data);
      this.list=response.data;
    },
    async updateItem(id,quantity){
      const response = await this.axios.patch(`http://localhost:3004/cart/${id}`,{'Quantity': quantity},{
        headers: {
        'Content-Type': 'application/json'
        },
      })
      .catch( (error) => alert('Error ', error.message));
      console.log(response.data);
      this.getData();
    },
    async removeItem(id){
      const response = await this.axios.delete(`http://localhost:3004/cart/${id}`)
      .catch( (error) => alert('Error ', error.message));
      console.log(response.data);
    },
    async getSummary(){
      const response = await this.axios.get("http://localhost:3004/summary")
      .catch( (error) => alert('Error ', error.message));
      console.log(response.data);
      this.cartSummary=response.data;
    }
  },
  created(){
    this.getData()
    this.getSummary()
  }
}
</script>

<style>
@import "./styles/bootstrap.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
