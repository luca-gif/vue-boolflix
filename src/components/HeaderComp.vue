<template>

    <header class="d-flex justify-content-between align-items-center mb-5">

      <div class="logo"><img src="../assets/img/Boolflix.png" alt=""></div>

      <div class="categoria d-flex">
        <h5 @click="cambioCategoria('')">Home</h5>
        <h5 @click="cambioCategoria('tv')">Serie Tv</h5>
        <h5 @click="cambioCategoria('movie')">Film</h5>
      </div>

      <div class="search w-25 d-flex">
        <input @keyup.enter="ricercaValore()" v-model.trim="ricerca" class="form-control d-inline-block mx-2" type="text">
        <button @click="ricercaValore()" class="btn btn-danger d-inline-block text-black">Search</button>
      </div>

    </header>
</template>

<script>

export default {
  name: 'HeaderComp',
  
  data(){
    return{
      ricerca: '',
    }
  },
  methods:{
    ricercaValore(){
      this.$emit('elementoCercato', this.ricerca);
      this.ricerca = '';
    },

    cambioCategoria(valoreStr){
      this.$emit('passoValore', valoreStr );
    }
  }
}
</script>

<style lang="scss" scoped>

header{
  height: 80px;
  background-color: black;
  padding: 0 20px;
  img{
    width: 140px;
    cursor: pointer;
  }

    input{
    background-color: rgb(228, 228, 228);
  }
  
  .categoria{
    color: rgb(201, 201, 201);
    h5{
      padding: 0 15px;
      cursor: pointer;
    }
  }
}

</style>