<template>
   
  <main>
    <div class="host-detail">
        <div class="house-details">
        <div class="house-title">
            <h1>{{host.title}}</h1>
            <div class="row">
                <div>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star-half-alt"></i>
                    <i class="far fa-star"></i>
                    <span>245 Reviews</span>
                </div>
                <div>
                    <p>Location: {{host.address}}</p>
                </div>
            </div>
        </div>
        <div class="gallery">
            <div class="gallery-img-1"><img :src="host.photo"></div>

        </div>
        <div class="small-details">
            <h2>Entire rental unit hosted by {{host.owner}}</h2>
            <p>2 guest &nbsp; &nbsp; 2 beds &nbsp; &nbsp; 1 bathroom</p>
            <h4>$ {{host.price}} / day</h4>
        </div>

        <hr class="line">

        <form class="check-form">
            <div>
                <label>Check-In</label>
                <input v-model="checkInDate" type="date" placeholder="Add date">
            </div>
            <div>
                <label>Check-Out</label>
                <input v-model="checkOutDate" type="date" placeholder="Add date">
            </div>
            <div class="guest-field">
                <label>Guest</label>
                <input  v-model="guestNumber" type="text" placeholder="Guests">
            </div>
            <div >
                <label>Price</label>
                <p>${{price}}</p>
            </div>
           
            <nuxt-link to="/reservation/">Make Reservation</nuxt-link>

        </form>

        <ul class="details-list">
            <li v-for="feature in host.features" :key="feature"><i class="fas fa-home"></i>{{features.toString()}}
        
            </li>
        </ul>

        <hr class="line">


        <p class="home-desc">Guests will be allocated on the ground floor according to availability. You get a comfortable {{host.roomNumber}} rooms apartment has a true city feeling. The price quoted is for two guest, at the guest slot please mark the number of guests to get the exact price for groups. The Guests will be allocated ground floor according to availability. You get the comfortable two bedroom apartment that has a true city feeling.</p>
        <hr class="line">

        <div class="map">
            <h3>Location on map</h3>
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d21221.676224044128!2d-122.45917885570059!3d37.75203368896406!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80859a6d00690021%3A0x4a501367f076adff!2sSan%20Francisco%2C%20CA%2C%20USA!5e0!3m2!1sen!2sin!4v1641145357317!5m2!1sen!2sin" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
            <b>{{host.address}}</b>
            <p>It's like a home away from home.</p>
        </div>

        <hr class="line">

        <div class="host">
            <img src="../../static/images/host.png">
            <div>
                <h2>Hosted by {{host.owner}}</h2>
                <p><span>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star-half-alt"></i>
                </span>&nbsp; &nbsp; 245 reviews &nbsp; &nbsp; Response rate 100% &nbsp; &nbsp; Response time: 60 min</p>
            </div>
        </div>
        <a href="#" class="contact-host">Contact Host</a>
    </div>
    <div class="container">
        <div class="footer">
            <a href="https://facebook.com/"><i class="fab fa-facebook-f"></i></a>
            <a href="https://youtube.com/"><i class="fab fa-youtube"></i></a>
            <a href="https://twitter.com/"><i class="fab fa-twitter"></i></a>
            <a href="https://linkedin.com/"><i class="fab fa-linkedin-in"></i></a>
            <a href="https://instagram.com/"><i class="fab fa-instagram"></i></a>
            <hr>
            <p>Copyright © 2021, Easy Tutorials.</p>
        </div>
    </div>

    </div>

  </main>  
</template>


<script>
import Navbar from '../../components/Navbar.vue';    
export default {
  components:{Navbar},
  async asyncData({ $axios, params }) {
    try {
      let singleHost = $axios.$get(`/api/hosts/${params.id}`);
      const [hostResponse] = await Promise.all([
        singleHost
      ]);
      return {
        host: hostResponse.host,
        features: hostResponse.host.features
      };
    } catch (err) {
      console.log(err);
    }
  } ,
  data(){
    return{
      isOpen:false,
      checkInDate:null,
      checkOutDate:null, 
      dateRange:null,
      guestNumber:null
    }
  },

  computed:{
    price(){

      let checkInDay = new Date(this.checkInDate).getTime()  
      let checkOutDay = new Date(this.checkOutDate).getTime() 
      if( checkOutDay - checkInDay > 0){
        this.dateRange = ( checkOutDay - checkInDay) / 86400000 
        return  this.dateRange*this.guestNumber*this.host.price
      } else{
        return null
      }

    }
    
  }
  

}
</script>


<style scoped>
  /*  @import '../../static/css/product-page.css'; */    

  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins', sans-serif;
}
.header{
    min-height: 100vh;
    width: 100%;
    background-image: linear-gradient(rgba(0,0,0,0.3),rgba(0,0,0,0.3)),url(../../static/images/banner.png);
    background-size: cover;
    background-position: center;
}

.container{
    padding: 0 7%;
}
.header h1{
    font-size: 4vw;
    font-weight: 500;
    color: #fff;
    text-align: center;
    padding-top: 22%;
}


/* -----footer------- */
.footer{
    margin: 80px 0 10px;
    text-align: center;
}
.footer a{
    text-decoration: none;
    color: #999;
    font-size: 22px;
    margin: 0 10px;
}
.footer hr{
    background: #999;
    height: 1px;
    width: 100%;
    border: 0;
    margin: 20px 0;
}
.footer p{
    padding-bottom: 15px;
}

.active{
    position: relative;
}
.active::after{
    content: '';
    background: #fff;
    width: 25px;
    height: 2px;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    bottom: -12px;
    border-radius: 2px;
}


.list-container{
    margin-top: 50px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.left-col{
    flex-basis: 70%;
}
.right-col{
    flex-basis: 25%;
}
.left-col h1{
    color: #333;
    font-weight: 600;
    margin-bottom: 30px;
}
.house{
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 30px 0;
    border-top: 1px solid #ccc;
}
.house-img{
    flex-basis: 40%;
}
.house-info{
    flex-basis: 58%;
    color: #555;
}
.house-img img{
    width: 100%;
    border-radius: 12px;
}
.house-info h3{
    font-weight: 600;
    color: #333;
    font-size: 22px;
    margin: 4px 0;
}
.house-info i{
    color: #ff5361;
    font-size: 18px;
    margin: 10px 1px;
}
.house-price{
    text-align: right;
}
.house-price h4{
    font-size: 20px;
}
.house-price h4 span{
    font-size: 16px;
    font-weight: 500;
}



/* ----------house-details page------------- */
.house-details{
    padding: 0 12%;
}
.house-title{
    margin-top: 50px;
}
.house-title h1{
    font-weight: 600;
}
.house-title .row{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    margin: 10px 0;
}
.house-title span{
    margin: 0 20px;
}
.house-title i{
    color: #ff5361;
    font-size: 14px;
}
.gallery{
    display: grid;
    grid-gap: 10px;
    grid-template-areas: 'first first . .' 'first first . .';
    margin: 20px 0;
}
.gallery div img{
    width: 55%;
    display: block;
    border-radius: 10px;
}
.gallery-img-1{
    grid-area: first;
}
.small-details h2{
    font-weight: 500;
}
.small-details h4{
    text-align: right;
    font-size: 22px;
}
.line{
    border: 0;
    height: 1px;
    background: #ccc;
    width: 100%;
    max-width: 800px;
    margin: 20px 0 50px;
}
.check-form{
    margin: 30px 0;
    background: #fff;
    box-shadow: 0 0 30px rgba(0,0,0,0.3);
    border-radius: 8px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    padding: 10px 50px;
}
.check-form label{
    display: block;
}
.check-form div{
    padding: 20px;
}
.check-form input{
    background: transparent;
    border: 0;
    outline: none;
}
.check-form button{
    background: #ff5361;
    border: 0;
    outline: none;
    color: #fff;
    padding: 18px;
    width: 350px;
    border-radius: 8px;
    font-size: 16px;
}

.check-form a{
    background: #ff5361;
    border: 0;
    outline: none;
    color: #fff;
    padding: 18px 105px;
    width: 350px;
    border-radius: 8px;
    font-size: 16px;
    text-decoration: none;
}


.guest-field{
    flex: 1;
}
.details-list{
    list-style: none;
    margin: 50px 0;
}
.details-list li{
    margin-left: 50px;
    font-size: 20px;
    font-weight: 500;
    margin-bottom: 20px;
    color: #555;
    position: relative;
}
.details-list li span{
    display: block;
    font-weight: 400;
    font-size: 16px;
}
.details-list li i{
    position: absolute;
    top: 5px;
    left: -40px;
}
.home-desc{
    max-width: 700px;
    margin-bottom: 50px;
}
.map{
    margin: 50px 0;
}
.map iframe{
    width: 100%;
    margin-bottom: 30px;
}
.map h3{
    font-size: 26px;
    font-weight: 500;
    margin-bottom: 30px;
}
.map b{
    display: block;
    margin-bottom: 16px;
}

.host{
    display: flex;
    align-items: center;
}
.host img{
    width: 80px;
    border-radius: 50%;
    margin-right: 30px;
}
.host h2{
    margin-bottom: 10px;
    font-weight: 500;
}
.host i{
    color: #ff5361;
}
.contact-host{
    display: inline-block;
    margin: 40px 0 40px 120px;
    text-decoration: none;
    color: #555;
    padding: 15px 50px;
    border: 1px solid #ff5361;
    border-radius: 8px;
}
/* -----media query for house details page---------- */
@media only screen and (max-width: 700px){
    .house-details{
        margin-top: 150px;
    }
    .row p{
        margin-top: 10px;
    }
    .gallery{
        grid-template-areas: 'first first' '. .' '. .';
    }
    .small-details h2{
        font-size: 20px;
        margin-top: 24px;
    }
    .small-details h4{
        text-align: left;
        margin: 10px 0;
        font-size: 18px;
    }
    .check-form{
        padding: 10px 30px;
    }
    .check-form div{
        padding: 20px 0;
        width: 100%;
    }
    .check-form input{
        border-bottom: 1px solid #ccc;
        width: 100%;
        padding-bottom: 5px;
    }
    .check-form button{
        font-size: 14px;
        margin-top: 10px;
        margin-bottom: 15px;
        border-radius: 4px;
    }

    .check-form a{
        font-size: 14px;
        margin-top: 10px;
        margin-bottom: 15px;
        border-radius: 4px;
    }

    .host{
        display: block;
        line-height: 28px;
    }
    .contact-host{
        margin: 40px 0;
    }
}


</style>