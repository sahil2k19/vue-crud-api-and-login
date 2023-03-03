<template>
  <div>
  <img alt="restro logo" src="../assets/restroLogo.jpg" class="restroLogo">

    <h1>SignUp</h1>

    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name">
        <input type="Email" v-model="email"  placeholder="Enter Email">
        <input type="Password" v-model="password" placeholder="Enter Password">
        <button class="signupButton" @click="signUp">Sign UP</button>

    </div>
  </div>
  
</template>

<script>

import axios from 'axios'

export default {
    name:"SignUp",
    data(){
      return{
        name:"",
        email:"",
        password:"",
      }
    },
    
    methods:{
     async signUp(){
        
        console.log("SignUP")
        let result = await axios.post("http://localhost:3000/user", {
          email:this.email,
          name:this.name,
          password:this.password,
        });
        console.log(result);
        if(result.status==201){
          alert("sign up successfully");
          localStorage.setItem("user-info", JSON.stringify(result.data));
          this.$router.push({name:"Home"})
        }
      },
    },
    mounted(){
      console.warn("mounted")
      let user = localStorage.getItem("user-info");
      if(user){
        this.$router.push({name:"Home"});
      }
    }
}



</script>


<style>
  

    

</style>