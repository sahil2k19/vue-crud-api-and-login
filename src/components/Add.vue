


<template>
  <div>
    <Header/>
    <h1>Hello User, Welcome on Add Restaurent Pages</h1>
    <form class="add">
      <input type="text" placeholder="Enter Name" v-model="restaurent.name" name="name">
      <input type="text" placeholder="Enter Address" v-model="restaurent.address" name="address">
      <input type="text" placeholder="Enter Contact No." v-model="restaurent.contact" name="contact">
      <button class="addButton" type="button" @click="addRestaurent"> Add new Restaurent </button>
    </form>
  </div>
</template>

<script>

import Header from "./Header.vue"
import axios from "axios"
export default {
    name: "AddView",
    components:{
      Header,
    },
    data(){
      return {
          restaurent:{
            name:"",
            address:"",
            contact:"",
          }
      }
    },  
    methods:{
      async addRestaurent(){
        console.log(this.restaurent)
        const result = await axios.post("http://localhost:3000/restaurent/",
          {
            name:this.restaurent.name,
            address:this.restaurent.address,
            contact:this.restaurent.contact,
          })
          console.log(result)
          if(result.status==201){
            this.$router.push({name:"Home"})
          }
      },
    },
    mounted(){
      let user = localStorage.getItem("user-info");
      if(!user){
        this.$router.push({name:"SignUp"});
      }
    }
}
</script>

<style>

</style>


