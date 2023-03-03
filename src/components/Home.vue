<template>
  <div>

    <Header/>
    <h1>Hello {{ name }}</h1>
    <table border="1">
    <tr>
      <td>Id</td>
      <td>Name</td>
      <td>Address</td>
      <td>Contact</td>
      <td>Action</td>
    </tr>

    <tr v-for="res in restaurent" :key="res.id">
      <td>{{ res.id }}</td>
      <td>{{ res.name }}</td>
      <td>{{ res.address }}</td>
      <td>{{ res.contact }}</td>
      <td><router-link :to="'/update/'+res.id">update</router-link></td>

    </tr>
    </table>
    <br>
    <br>
    <br>

    <div class="container-fluid">
      <div class="row">
        <div class="col-6 bg-primary">jflksajfdlksaf</div>
        <div class="col-6 bg-secondary">ksjdflkdsajflak</div>
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios'
import Header from "./Header.vue"

export default {
    name: "HomeView",
    data(){
      return{
        name:"",
        restaurent:[],
      }
    },
    components:{
      Header,
    },
    async mounted(){
      console.warn("mounted")
      
      // all restaurent result 
      let result = await axios.get("http://localhost:3000/restaurent");
      console.log(result);
      this.restaurent = result.data;

      let user = localStorage.getItem("user-info");

      this.name = JSON.parse(user).name;
      if(!user){
        this.$router.push({name:"SignUp"});
      }
    }
}
</script>

<style>
  td{
    width:160px;
    height:40px;
  }

</style>


