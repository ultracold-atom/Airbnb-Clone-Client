<template>
  <main>
    
    <div class="user-icon">
      <div class="lines">
        <div class="line"></div>
        <div class="line"></div>
        <div class="line"></div>   
      </div>

      <a @click="onClick" href="#">
        <img class="icon" src="/images/user.png" alt=""/>
      </a>

      <div v-if="isOpen" class="dropdown-content">
        <li> <nuxt-link to="/signup">Sign Up</nuxt-link> </li>
        <li> <nuxt-link to="/login">Sign In</nuxt-link> </li>

        <li v-if="$auth.$state.loggedIn" @click="onLogout"><a href="#">Logout</a></li>
        <li v-else ><a href="#">Help</a></li>

        <li><a href="#">Become a Host</a></li>
        <li><a href="#">Experience a Host</a></li>                
      </div>
    </div>

    

  </main>  
</template>


<script>
export default {
  props:["isOpen"],
  methods:{
    onClick(){
      this.isOpen = !this.isOpen
    },
    async onLogout() {
      await this.$auth.logout();
    }
  }
}
</script>



<style>

body {
  background-color: white;
  margin: 0;
}

.user-icon { 
  cursor: pointer;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: white;
  height: 38px;
  width: 76px;
  border-radius: 18px;
  border: 1.6px solid #EBEBEB;   
  margin-top: 10px;
  margin-left: 20px; 
  padding-left: 4px;
}


.line{
  background-color: #484848; 
  width: 16px;
  height: 1.5px;
  margin: 2.4px;
}

.icon {
  width: 30px;
}

/*
a:focus + .dropdown-content{
  display: flex;
  flex-direction: column;
  justify-content: space-around;

}    */


.dropdown-content {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  z-index: 2;
  position: fixed;
  right: 20px;
  top: 75px;
  background-color: white;
  width: 170px;
  height: 180px;
  border-radius: 13px;
  box-shadow: 0px 8px 16px 0px #EBEBEB;
  padding-top: 10px;
}

.dropdown-content li {
  list-style: none;
}

.dropdown-content li a {
  color: #484848;
  text-decoration: none;
}

.dropdown-content li:hover {
  background-color: #f7f7f7;
}



</style>