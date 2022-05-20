<template>
  <div>

    <div class="search d-flex py-4 justify-content-center">

    <input @keyup.enter="$emit('elementoCercato', ricerca)" v-model.trim="ricerca" class="form-control w-25  mx-2" type="text">
    <button @click="$emit('elementoCercato', ricerca)" class="btn btn-danger text-black">Search</button>

    </div>

  </div>
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



</style>