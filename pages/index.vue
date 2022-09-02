<template>
  <main>
    <div class="header-main">
      <Navbar />
      <Category />
      <div class="hosts">
        <div v-for="host in hosts" :key="host" class="host">
          <nuxt-link :to="`/hosts/${host._id}`" class="host-country">
            <img :src="host.photo" class="host-photo">
            <h4 class="host-country">{{host.country}}</h4>            
          </nuxt-link>
        </div>
      </div> 

    </div>
  </main>

</template>

<script>
import Navbar from '../components/Navbar.vue';
import Category from '../components/Category.vue';
import Menu from '../components/menu.vue'
export default {
  name: 'IndexPage',
  components:{
    Navbar,
    Category,
    Menu
  },
  async asyncData({ $axios }) {
    try {
      let response = await $axios.$get("/api/hosts");
      console.log(response);
      return {
        hosts: response.hosts
      };
    } catch (err) {
      console.log(err);
    }
  }
}
</script>


<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins', sans-serif;
}


.header-main{
    min-height: 100vh;
    width: 100%;
    background-color: #fff;
    background-size: cover;
    background-position: center;
}

.hosts{
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  flex-wrap: wrap;
  margin-top: 3rem;
}

.host{
  margin-top: 20px;
}

.host a{
  text-decoration: none;
  color: black;
}

.host-photo{
  width: 20.6rem;
  height: 19rem;
  border-radius: 10px;
}

.host-country{
  margin-top: 5px;
  font-family: "Roboto",sans-serif;
  font-size: 19px;
}

</style>

