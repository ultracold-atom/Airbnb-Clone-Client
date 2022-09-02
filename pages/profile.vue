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
          <div class="buttons">
            <button class="upload-host" @click="onUpdateProfile">Update Profile</button>  
            <button class="upload-host" @click="onLogout">Logout</button>  
          </div>
    
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
    async onUpdateProfile() {
      let data = {
        firstName: this.firstName,
        secondName: this.secondName,
        gender: this.gender,
        email: this.email,
        password: this.password
      };
      try {
        let response = await this.$axios.$put("/api/auth/user", data);
        if (response.success) {
          this.name = "";
          this.email = "";
          this.password = "";
          await this.$auth.fetchUser();
        }
      } catch (err) {
        console.log(err);
      }
    },
    async onLogout() {
      await this.$auth.logout();
    }
  }
};
</script>


<style scoped>

  @import '../static/css/signup.css';

  .buttons{
    margin-right: 60px;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

</style>