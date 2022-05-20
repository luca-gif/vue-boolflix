<template>
  <div>
    
    <h3>{{titolo}}</h3>
    <p>{{titoloOriginale}}</p>
    <p>{{lingua}}</p>
    <p>{{voto}}</p>

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