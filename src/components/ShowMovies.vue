<template>
  <div>

    <div class="mini-wrapper">

        <div class="lm-card d-flex align-items-center">

          <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w200${image}`" alt="">  
          </div>

        
        <div class="text px-4 d-flex flex-column">

            <h6>{{titolo}}</h6>
           <p v-if="lingua === 'it'">Lingua: <img src="../assets/img/Flag_of_Italy.svg.png" alt="UK flag"> </p>
            <p v-else-if="lingua === 'en'|| lingua === 'uk'">Lingua: <img src="../assets/img/uk.png" alt="UK flag"> </p>
            <p v-else> Lingua: {{lingua}}</p>
            <p>Voto: {{voto}}</p>

        </div>

        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShowMovies',
  props:{
    titolo: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
    image: String
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
    width: 120px;
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

  img{
    width: 30px;
    height: 20px;
    border-radius: 2px;
  }
}

</style>