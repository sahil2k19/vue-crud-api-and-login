<template>
  <div>
    <Header/>
    <h1>Hello User, Welcome on Update Restaurent Pages</h1>
    <form class="update">
      <input type="text" placeholder="Enter Name" v-model="restaurent.name" name="name">
      <input type="text" placeholder="Enter Address" v-model="restaurent.address" name="address">
      <input type="text" placeholder="Enter Contact No." v-model="restaurent.contact" name="contact">
      <button class="updateButton" type="button" @click="updateRestaurent"> Update Restaurent </button>
    </form>
  </div>
</template>

<script>
import Header from "./Header.vue"

import axios from "axios";

export default {
    name: "UpdateView",
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
      async updateRestaurent(){
        console.log(this.restaurent);
        const result = await axios.put("http://localhost:3000/restaurent/"+this.$route.params.id,
          {
            name:this.restaurent.name,
            address:this.restaurent.address,
            contact:this.restaurent.contact,
          }
        );
        if(result.status==200){
          this.$router.push({name:"Home"})
        }
      } 
    },
    async mounted(){
      let user = localStorage.getItem("user-info");
      if(!user){
        this.$router.push({name:"SignUp"});
      }    
      let result = await axios.get("http://localhost:3000/restaurent/"+this.$route.params.id)
      console.log(this.$route.params)
      console.log(result.data);
      this.restaurent = result.data
    }
}
</script>

<style>

</style>



