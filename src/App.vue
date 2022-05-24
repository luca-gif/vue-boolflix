<template>
  <div>

    <div v-if="isLoaded">
    <header-comp @passoValore="passoValore" @elementoCercato="valorePassato" />

           <main-comp
           :arrayPopularFilms="popularFilms"  
           />

           <main-comp v-if="films.length > 0"
           :arrayFilms="films"
           />
        
           <main-comp v-if="tvSeries.length > 0"
           :arrayTv="tvSeries"
           />

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

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
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
    passoValore(type){
      this.type = type;
      this.apiMovies(type);
    },
    apiMovies(type){
          axios.get(this.moviesUrl + type, {
          params: this.moviesParams
        } )
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

    valorePassato(nomeValore){
      this.moviesParams.query = nomeValore;
      console.log(this.type)

      if(this.type === ''){
        this.apiMovies('movie');
        this.apiMovies('tv');
      }else{
        this.apiMovies(this.type);
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

    
</style>
