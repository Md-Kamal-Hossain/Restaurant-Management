<template>
<img class="cup" src="../assets/cup.png">
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" v-model="name" placeholder="Enter Name"/>
    <input type="text" v-model="email" placeholder="Email"/>
    <input type="Password" v-model="password" placeholder="Password"/>
    <button v-on:click="signUp">Sign Up</button>
  </div>
  </template>
<script>
import axios from 'axios'
export default{
    name: 'SignUp',
  data() {
    return {
      name: '',
      email: '',
      password: ''
    };
  },
    methods: {
        async signUp() {
        
            let result = await axios.post("http://localhost:3000/user", {
            name: this.name, email: this.email, password: this.password
            
            });
            console.warn(result);
            if(result.status==201)
            {
              alert("Sign up succes");
              localStorage.setItem("User-info",JSON.stringify(result.data));
            }
        
        
        }

  }

}
</script>


<style>
.cup {
  width: 100px;
  height: 100px;
}
.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid blue;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid green;
    background:red;
    color: green;
    cursor:pointer;
}

</style>
