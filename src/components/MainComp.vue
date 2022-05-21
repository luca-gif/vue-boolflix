<template>
  <div>

     <h3 class="text-danger px-5 pt-4">Most Popular</h3>
     <div class="films popular-films py-3 d-flex">


    <div v-for="popularFilm in arrayPopularFilms" class="most-popular" :key="popularFilm.id">

      <ShowPopularMovies
      :titolo="popularFilm.title"
      :titoloOriginale="popularFilm.original_title"
      :lingua="popularFilm.original_language"
      :voto="popularFilm.vote_average"
      :image="popularFilm.poster_path"
      />

    </div>

  </div>
      
    <div class="films searched-films py-3 d-flex">
      
      <div v-for="film in arrayFilms" :key="film.id">
    
      <show-movies
      :titolo="film.title"
      :titoloOriginale="film.original_title"
      :lingua="film.original_language"
      :voto="film.vote_average"
      :image="film.poster_path"
      />
    </div>

    </div>

       
  </div>
</template>

<script>
import ShowMovies from './ShowMovies.vue';
import ShowPopularMovies from './ShowPopularMovies.vue';

export default {
  components: { ShowMovies, ShowPopularMovies },
  name: 'MainComp',

   props:{
    arrayFilms: Array,
    arrayPopularFilms: Array
  },
}
</script>


<style lang="scss" scoped>

  .films{
    width: 95%;
    margin: auto;
    overflow-x: auto;
  }

</style>