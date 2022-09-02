<template>
  <main>
    <Navbar />

    <div class="reservation">
      <div class="reservation-section">
        <h3 class="form-heading">Congratulations</h3>
        <p>You just made your reservation! Your reservation will send to the Host</p> 
      </div>  
    </div>
  </main>  
</template>

<script>
import Navbar from '../components/Navbar.vue';    
export default {
  components:{Navbar}  
}
</script>


<style>

body{
    margin: 0px 0px;
    font-family: Roboto, Helvetica, sans-serif;
    color: #484848;
    background-color: white;
 }
 
 
 h3{
     font-size: 24px;
     line-height: 1.25em;
 }
 
 p{
     font-size: 16px;
     line-height: 1.75em;
 }

 .reservation{
  display: flex;
  flex-direction: row; 
  border: 1.5px solid #B0B0B0;
  border-radius: 5px;
}

.reservation-section{
    width: 34.5rem;
    height: 28.625rem;
    background-color: #ffffff;
    padding-left: 40px;
    padding-top : 30px;
    border: 2px solid #484848;
    border-radius: 17px;
    margin-top: 20px;
    margin-left: 30rem;    
}

.form-heading{
    color: #484848 !important;
    font-size: 40px;
    line-height: 40px;
    letter-spacing: -0.6px;
    margin: 7% 18%;
}



</style>