<template>
  <main>
    <Navbar />
    <div class="cards">

        <div class="form-section">
          <h1 class="form-heading">Become a Part of Airbnb </h1>
          <h2 class="form-subheading">Tell us a little about yourself</h2>
          <input v-model="firstName" class="location" placeholder="First Name"/>
          <input v-model="secondName" class="location" placeholder="Second Name"/>
          <select  v-model="gender" class="location" name="Gender" >
            <option value="" disabled selected>Gender</option>
            <option  v-for="gender in genders" :key="gender"  :value="gender">{{gender}}</option>
          </select>          
          <input v-model="email" class="location" placeholder="E-mail"/>         
          <input v-model="password" class="location" placeholder="Password" />   
          <button class="upload-host" @click="onSignup">Sign Up</button>        
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
      genders: ["Male","Female","Other"],
      firstName: "",
      secondName: "",
      gender: "",
      email: "",
      password: ""
    };
  },
  methods: {
    async onSignup() {
      try {
        let data = {
          firstName: this.firstName,
          secondName: this.secondName,
          gender: this.gender,
          email: this.email,
          password: this.password
        };
        let response = await this.$axios.$post("/api/auth/signup", data);
        console.log(response);
        if (response.success) {
          this.$auth.loginWith("local", {
            data: {
              email: this.email,
              password: this.password
            }
          });
          this.$router.push("/");
        }
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>



<style scoped>

  @import '../static/css/signup.css';

</style>