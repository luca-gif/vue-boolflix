<template>
  <div>
      
    <div v-for="film in arrayFilms" :key="film.id">
    
      <show-movies
      :titolo="film.title"
      :titoloOriginale="film.original_title"
      :lingua="film.original_language"
      :voto="film.vote_count"
      />
    </div>

  </div>
</template>

<script>
import ShowMovies from './ShowMovies.vue';

export default {
  components: { ShowMovies },
  name: 'MainComp',

   props:{
    arrayFilms: Array
  },
}
</script>

<style lang="scss" scoped>

</style>