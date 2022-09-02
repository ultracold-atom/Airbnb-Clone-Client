<template>
  <main>
    <Navbar />
    <div class="cards">

        <div class="form-section">
          <h1 class="form-heading">Login to Airbnb </h1>
          <h2 class="form-subheading">Login to the Airbnb World</h2>          
          <input v-model="email" class="location" placeholder="E-mail"/>         
          <input v-model="password" class="location" placeholder="Password" />   
          <button class="upload-host" @click="onLogin">Login</button>        
        </div>

    </div>     
  </main>  
</template>


<script>
import Navbar from '../components/Navbar.vue';
export default {
  components:{
    Navbar  
  },
  middleware: "auth",
  auth: "guest",
  layout: "none",
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    async onLogin() {
      try {
        this.$auth.loginWith("local", {
          data: {
            email: this.email,
            password: this.password
          }
        });
        this.$router.push("/");
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>


<style>

  @import '../static/css/login.css';

</style>