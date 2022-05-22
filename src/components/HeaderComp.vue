<template>

    <header class="d-flex justify-content-between align-items-center">

      <div class="logo"><img src="../assets/img/Boolflix.png" alt=""></div>

      <div class="categoria d-flex">
        <h5>Serie Tv</h5>
        <h5>Film</h5>
      </div>

      <div class="search w-25 d-flex">
        <input @keyup.enter="$emit('elementoCercato', ricerca)" v-model.trim="ricerca" class="form-control d-inline-block mx-2"  type="text">
        <button @click="$emit('elementoCercato', ricerca)" class="btn btn-danger d-inline-block text-black">Search</button>
      </div>

      
    </header>
</template>

<script>

export default {
  name: 'HeaderComp',

  data(){
    return{
      ricerca: ''
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
      padding: 0 10px;
      cursor: pointer;
    }
  }
}



</style>