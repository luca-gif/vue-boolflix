<template>
  <div>

    <div v-if="isLoaded">
    <header-comp @elementoCercato="valorePassato" />

           <main-comp
           :arrayFilms="films"
           :arrayPopularFilms="popularFilms"
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
    MainComp
  },

  data(){
    return{
      moviesUrl: 'https://api.themoviedb.org/3/search/movie',
      popularMoviesUrl:'https://api.themoviedb.org/3/movie/popular?api_key=83c397b63c322fd6a37d6c5ec3d5f6de',
      moviesParams: {
        api_key: '83c397b63c322fd6a37d6c5ec3d5f6de',
        language: 'it-IT',
        query: '',
      },
      
      films: [],
      popularFilms: [],
      isLoaded: true, //Cambiare in false
       
    }
  },
  
  methods:{

    /* Chiamata per i film */

    apiMovies(){
      axios.get(this.moviesUrl, {
        params: this.moviesParams
      } )
      .then(r =>{
        this.films = r.data.results;
        console.log(this.films)
      })
    },

    /* Chiamata per i film piu popolari */

    popularMovies(){
      axios.get(this.popularMoviesUrl)
      .then(r =>{
        this.popularFilms = r.data.results;
        console.log(this.popularFilms)
      })
    },

    valorePassato(nomeValore){
      this.moviesParams.query = nomeValore;
      this.apiMovies();
      console.log(this.moviesParams.query);
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
