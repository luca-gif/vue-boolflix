<template>
  <div>

    <div v-if="isLoaded">
    <header-comp @passoValore="mostraSezioni" @elementoCercato="iniziaRicerca" />

    <JumboComponent
    :arrPopular="popularFilms"
    />

        <div class="most-popular">
          <h3 v-if="popularFilms.length > 0" class="text-danger px-5">Popular Movies</h3>
           <main-comp
           :arrayPopularFilms="popularFilms"  
           />
        </div>

        <div v-if="type == '' || type == 'movie'" class="films">
          <h3 v-if="films.length > 0" class="text-danger px-5">Films</h3>
           <main-comp
           :arrayFilms="films"
           />
        </div>

        <div v-if="type == '' || type == 'tv'" class="tv-series">
          <h3 v-if="tvSeries.length > 0 " class="text-danger px-5">Serie Tv</h3>
           <main-comp
           :arrayTv="tvSeries"
           />
        </div>

    </div>

    <div v-else class="loading">
      <audio autoplay src="./assets/Sound/Netflix-Intro-Sound-Effect.mp3" type="audio/mpeg"></audio>
    </div>

  </div>
</template>

<script>
import axios from 'axios'
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
import JumboComponent from './components/JumboComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
    JumboComponent
},

  data(){
    return{
      popularMoviesUrl:'https://api.themoviedb.org/3/trending/movie/week?api_key=83c397b63c322fd6a37d6c5ec3d5f6de',

      moviesUrl: 'https://api.themoviedb.org/3/search/',
      type: '',
      moviesParams: {
        api_key: '83c397b63c322fd6a37d6c5ec3d5f6de',
        language: 'it-IT',
        query: '',
      },
      films: [],
      tvSeries: [],
      popularFilms: [],
      isLoaded: false, //Cambiare in false
    }
  },
  
  methods:{
    mostraSezioni(sezioneDaMostrare){
      this.type = sezioneDaMostrare;
    },
    apiUrl(type){
          axios.get(this.moviesUrl + type, {
          params: this.moviesParams
        })
        .then(r =>{
          if(type === 'movie'){
            this.films = r.data.results;
          console.log(this.films)

          }else {
            this.tvSeries = r.data.results;
          console.log(this.tvSeries)
          }
        })
    },

    /* Chiamata per i film piu popolari */

    popularMovies(){
      axios.get(this.popularMoviesUrl)
      .then(r =>{
        this.popularFilms = r.data.results;
        //console.log(this.popularFilms)
      })
    },

    iniziaRicerca(filtriRicerca){
      this.moviesParams.query = filtriRicerca;
      console.log(this.type)

      if(this.type === ''){
        this.apiUrl('movie');
        this.apiUrl('tv');
      }else{
        this.apiUrl(this.type);
      }
    },
 

    loadIsTrue(){
    this.isLoaded = true
    },
  },

  mounted(){
    setTimeout(this.loadIsTrue,4000)
    this.popularMovies()
  }

}
</script>

<style lang="scss">
  @import './assets/style/global';

  .loading{
    background-image: url(./assets/img/thibault-penin-AWOl7qqsffM-unsplash.jpg);
    background-position: center;
    background-size: cover;
    height: 100vh;
  }

  h3.text-danger{
    margin-top: 30px;
  }

</style>
