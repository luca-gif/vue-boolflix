<template>
  <div class="container">

    <header-comp @elementoCercato="valorePassato" />
    
    <main-comp
    :arrayFilms="films"
    />

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
      this.apiMovies()
      console.log(this.moviesParams.query);
    },

  },

 
}
</script>

<style lang="scss">
@import './assets/style/global';



</style>
