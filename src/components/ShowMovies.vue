<template>
  <div>
    
    <img :src="`https://image.tmdb.org/t/p/w200${image}`" alt="">
    <h3>Titolo: {{titolo}}</h3>
    <p>Titolo originale: {{titoloOriginale}}</p>
    <p>Lingua: {{lingua}}</p>
    <p>Voto: {{voto}}</p>
   

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

div{
  color: whitesmoke;
}

</style>