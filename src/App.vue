<template>
  <Navbar />
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
  <router-view
  :baseURL="baseURL"
  :products="products"
  :categories="categories"
  >
  </router-view>
</template>

<script>
import Navbar from "./components/Navbar.vue";

import axios from 'axios';
export default{
    components: {
      Navbar
    },
    data(){
      return{
        baseURL :"https://elnamat.com/efatora/api/vendors/",
        products:[],
        categories:[],
      }
    },
    methods: {
      async fetchData() {
      // api call to get the categories
        await axios.get(this.baseURL + "categotries")
        // await axios.get("https://elnamat.com/efatora/api/vendors/categotries")
        .then(res=>{
          this.categories=res.data})
        .catch((err)=>console.log('err',err));

        //api call to get the products
        await axios.get(this.baseURL + "products")
        .then(res=>{
          this.products=res.data})
        .catch((err)=>console.log('err',err));

      }
    },
    mounted() {
      this.fetchData();
    }
  };
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
