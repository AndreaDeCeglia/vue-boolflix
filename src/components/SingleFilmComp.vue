<template>

  <div class="card col-2 p-2">
    <img :src="`http://image.tmdb.org/t/p/w342/${ObjMovie.backdrop_path}`" class="card-img-top" alt=""/>
    <div class="card-body">
      <h5 class="card-title">{{ ObjMovie.title }}</h5>
      <p class="card-text">toh</p>
    </div>
  </div>
</template>

<script>
  export default {
      name: 'CardComp',
      props: {
          ObjMovie: Object
      }
  }
</script>

<style>

</style>