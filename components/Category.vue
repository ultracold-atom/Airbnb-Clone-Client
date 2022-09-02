<template>
  <main>
    <div class="filters">

      <div class="filter">
        <img src="/icons/olağanüstü.jpg" class="filter-icon"> 
        <h3 class="filter-type">Wonderful</h3>         
      </div>


      <div class="filter">
        <img src="/icons/national-park.jpg" class="filter-icon"> 
        <h3 class="filter-type">National Park</h3>         
      </div>

      <div class="filter">
        <img src="/icons/island.jpg" class="filter-icon"> 
        <h3 class="filter-type">Island</h3>         
      </div>

      <div class="filter">
        <img src="/icons/small-house.jpg" class="filter-icon"> 
        <h3 class="filter-type">Houses</h3>         
      </div>

      <div class="filter">
        <img src="/icons/north-pole.jpg" class="filter-icon"> 
        <h3 class="filter-type">North Pole</h3>         
      </div>

      <div class="filter">
        <img src="/icons/bungalov.jpg" class="filter-icon"> 
        <h3 class="filter-type">Bungalov</h3>         
      </div>

      <div class="filter">
        <img src="/icons/cave.jpg" class="filter-icon"> 
        <h3 class="filter-type">Cave</h3>         
      </div>

      <div class="filter">
        <img src="/icons/landscape.jpg" class="filter-icon"> 
        <h3 class="filter-type">Landscape</h3>         
      </div>

      <div class="filter">
        <img src="/icons/tropical.jpg" class="filter-icon"> 
        <h3 class="filter-type">Tropical</h3>         
      </div>

      <div class="filter">
        <img src="/icons/castle.jpg" class="filter-icon"> 
        <h3 class="filter-type">Castle</h3>         
      </div>

      <div class="filter">
        <img src="/icons/country.jpg" class="filter-icon"> 
        <h3 class="filter-type">Country</h3>         
      </div>

      <div class="filter">
        <img src="/icons/estate.jpg" class="filter-icon"> 
        <h3 class="filter-type">Estate</h3>         
      </div>

      <div class="filter">
        <img src="/icons/treehouse.jpg" class="filter-icon"> 
        <h3 class="filter-type">Tree House</h3>         
      </div>

    </div>
  </main>  
</template>



<style>
  .filters{
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    border-bottom: 1px solid #EBEBEB;    
    cursor: pointer;
}

.filter{
  display: flex;
  flex-direction: column;
  align-items: center;  
  opacity: 0.7;
}

.filter:hover{
  opacity: 1;  
}

.filter-icon{
  width: 1.6rem;  
  margin-bottom: 3px;
}

.filter-type{
  color: #484848;   
  font-size: 0.8rem;
}

</style>