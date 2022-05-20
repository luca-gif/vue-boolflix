<template>
  <div>

    <div class="mini-wrapper">

        <div class="lm-card d-flex align-items-center">

          <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w200${image}`" alt="">  
          </div>

        
        
        <div class="text px-4 d-flex flex-column">

            <h5>{{titolo}}</h5>
            <p>Titolo originale: {{titoloOriginale}}</p>
            <p>Lingua: {{lingua}}</p>
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
  border-radius: 10px;
  width: 400px;
  height: 220px;
  margin: 0 10px;
  padding-left: 10px;
  
  }

  img{
    border-radius: 10px;
    width: 120px;
    transition: all .5s;
    
    &:hover{
      scale: 105%;
  }
}

.text{
  color: rgb(186, 186, 186);
  font-size: .8rem;
}

</style>