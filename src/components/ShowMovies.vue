<template>
  <div>
    
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
    voto: Number
  }
}
</script>

<style lang="scss">

</style>