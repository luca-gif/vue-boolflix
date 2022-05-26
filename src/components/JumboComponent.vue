<template>
  <div class="jumbotron">

    <div v-for="wallpaper in arrPopular" :key="wallpaper">
      <img :src="`https://image.tmdb.org/t/p/original${setImg()}`" :alt="wallpaper.title">
    </div>

  </div>
</template>

<script>
export default {
  name: 'JumboComponent',
  props:{
    arrPopular: Array,
  },
  methods:{
    setImg(){
      for(let i=0; i<this.arrPopular.length; i++){
        return this.arrPopular[i].backdrop_path
      }
    },
    
  }
}
</script>

<style lang="scss" scoped>

  .jumbotron{
    margin-top: 80px;
    height: 300px;
    overflow: hidden;
    img{
      width: 1600px;
    }
  }

</style>