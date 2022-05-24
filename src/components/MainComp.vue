<template>
  <div>

     <!-- <h3 class="text-danger px-5 pt-4">Most Popular</h3> -->
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
        :type="type"
        :titolo="film.title"
        :titoloOriginale="film.original_title"
        :lingua="film.original_language"
        :voto="film.vote_average"
        :image="film.poster_path"
        />

      </div>

      <!-- Ciclo Serie Tv -->
      <div v-for="serieTv in arrayTv" :key="serieTv.id">
      
        <show-movies
        :type="type"
        :titoloTv="serieTv.name"
        :titoloOriginaleTv="serieTv.original_name"
        :linguaTv="serieTv.original_language"
        :votoTv="serieTv.vote_average"
        :imageTv="serieTv.poster_path"
        />

      </div>
    </div>
  </div>
  
</template>

<script>
import ShowPopularMovies from './ShowPopularMovies.vue';
import ShowMovies from './ShowMovies.vue';

export default {
  components: { ShowPopularMovies, ShowMovies },
  name: 'MainComp',

   props:{
    arrayFilms: Array,
    arrayPopularFilms: Array,
    arrayTv: Array,
    type: String
  },
}
</script>


<style lang="scss" scoped>

  .films{
    width: 95%;
    margin: auto;
    overflow-x: auto;
    margin-bottom: 40px;
  }

  ::-webkit-scrollbar {
    height: .5em;
  }

  ::-webkit-scrollbar-track{
     background: rgb(50, 50, 50);
     border-radius: 5px;
  }

   ::-webkit-scrollbar-thumb{
      background: hsl(0, 100%, 32%);
      border: .05em solid rgb(72, 72, 72);
      border-radius: 5px;
   }

     ::-webkit-scrollbar-thumb:hover{
      background: hsl(0, 100%, 35%);    
   }


</style>