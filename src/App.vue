<template>
  <div>

    <div v-if="isLoaded">
    <header-comp @elementoCercato="valorePassato" />
    
    <main-comp
    :arrayFilms="films"
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
      moviesParams: {
        api_key: '83c397b63c322fd6a37d6c5ec3d5f6de',
        language: 'it-IT',
        query: '',
      },
      films: [],
      isLoaded: false,
       
    }
  },
  
  methods:{
    apiMovies(){
      axios.get(this.moviesUrl, {
        params: this.moviesParams
      } )
      .then(r =>{
        this.films = r.data.results;
        console.log(this.films)
      })
    },

    valorePassato(nomeValore){
      this.moviesParams.query = nomeValore;
      this.apiMovies();
      console.log(this.moviesParams.query);
    },

    loadIsTrue(){
    this.isLoaded = true
    }

  },

  mounted(){
    setTimeout(this.loadIsTrue,3000)
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
