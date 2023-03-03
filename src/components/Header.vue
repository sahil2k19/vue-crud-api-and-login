<template>
  <div>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="add">Add Restaurent</router-link>
        <router-link @click="logout" to="#">Logout</router-link>
    </div>

  </div>
</template>

<script>
export default {
    name:'HeaderVue',

    methods:{
        logout(){
            console.log("logout");
            localStorage.clear();
            this.$router.push({name:"Login"})
        }
},
}
</script>

<style>
    .nav{
        background-color: #333;
        height:40px;
    }
    .nav a{
        float:left;
        color:#f2f2f2;
        text-align: center;
        padding:10px 14px;
        text-decoration:none;
        font-size:16px;
        margin-right:4px;

    }
    .nav a:hover{
        background-color:#ddd;
        color:#222;
    }
</style>