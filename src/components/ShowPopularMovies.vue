<template>
  <div>

    <div class="mini-wrapper">
        <div class="lm-card d-flex align-items-center">

          <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w200${image}`" :alt="titolo">  
          </div>
    
          <div class="text px-4 d-flex flex-column">

              <h6>{{titolo}}</h6>
              <p>Titolo originale: {{titoloOriginale}}</p>

              <p v-if="lingua === 'it'"><img src="https://www.countryflagicons.com/FLAT/32/IT.png"> </p>
              <p v-else-if="lingua === 'en'|| lingua === 'uk'">Lingua: <img src="https://www.countryflagicons.com/FLAT/32/GB.png"> </p>
              <p v-else> Lingua: {{lingua}}</p>
              
              <div class="stars-rating"> 
                
              <span  v-for="(star,index) in calcolaVoto()" :key="`c${index}`"><i class="fa-solid fa-star"></i></span>
              <span v-for="(emptyStar, index) in 5 - calcolaVoto()" :key="`d${index}`"><i class="fa-regular fa-star"></i></span>

              </div>
              
          </div>
        </div>
    </div>
   

  </div>
</template>

<script>
export default {
  name: 'ShowPopularMovies',
  props:{
    titolo: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
    image: String
  
  },
  methods:{
    calcolaVoto(){
      return Math.round(this.voto / 2)
    }
  }
}
</script>

<style lang="scss" scoped>

.lm-card{
  border: 1px solid rgb(180, 180, 180);
  background-color: black;
  border-radius: 10px;
  width: 350px;
  height: 200px;
  margin-right: 15px;
  padding-left: 10px;
  }

  .poster{

    img{
    border-radius: 10px;
    width: 100px;
    transition: all .4s;
    cursor: pointer;
    
      &:hover{
        scale: 105%;
    }
  }
}

.text{
  color: rgb(186, 186, 186);
  font-size: .7rem;
}


</style>