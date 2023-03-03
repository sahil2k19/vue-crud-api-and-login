<template>
  <div>
    <img class="logo" src = "../assets/restroLogo.jpg"/>
    <h1>Login</h1>
    <div class="login">
        <input type="text" v-model="email" placeholder="Enter Email">
        <input type="password" v-model="password" placeholder="Enter Password"/>
        <button @click="login" class="loginButton">Login</button>
    </div>
  </div>
</template>

<script>

import axios from "axios";

export default {
    name:"LoginVue",

    data(){
        return{
            email:"",
            password:"",
        }
    },
    methods:{
        async login(){
            let result  = await axios.get(`http://localhost:3000/user?email=${this.email}&password=${this.password}`)

            console.log(result);

            if(result.status == 200 && result.data.length >0){
                localStorage.setItem("user-info" ,JSON.stringify(result.data[0]))
                this.$router.push({name:"Home"});
            }
            
        }
    }
}
</script>

<style>
    .logo{
        width:176px;
    }
</style>