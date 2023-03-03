<template>
 <div>

  <!-- <SignUp/> -->
  <router-view/>

 </div>
</template>

<script>
// import SignUp from "./components/SignUp.vue"

export default {
  name: 'App',
  components: {
    // SignUp,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin:0;
  padding:0;
}
body{
  margin:0;
  padding:0;
  box-sizing: border-box ;
}
.register input, .login input , .add input , .update input{
        
        width: 348px;
        padding: 10px;
        display: block;
        margin-left: auto;
        margin-right: auto;
        margin-top: 20px;
        border: 1px solid #695454;
    
        }

.signupButton , .loginButton, .addButton ,.updateButton{
    padding: 10px;
    background: #1f1fb4;
    color: white;
    border-radius: 19px;
    width: 148px;
    border: 1px solid blue;
    margin-top: 24px;
    }

.restroLogo{
  width:100px;

}

</style>
