<template>

  <div id="SingleFilm">
    <div class="card-image">
      <img 
      :src="`http://image.tmdb.org/t/p/w342/${ObjMovie.backdrop_path}`" 
      alt="Movie Poster"
      />
    </div>
    
    <div class="card-body">
      <p class="card-title"> <b>Titolo: </b> {{ ObjMovie.title }}</p>
      <p class="card-title"> <b>Titolo Originale: </b> {{ ObjMovie.original_title }}</p>
      <p class="card-title"> <b>Voto: </b> {{ ObjMovie.vote_average }}</p>
      <!-- <p class="card-title"> <b>overview: </b> {{ ObjMovie.overview }}</p> -->
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

<style scoped lang="scss">

#SingleFilm{
  width: 342px;
  //position: relative;
}

.card-body{
  display: none;
  //position: absolute;
  top: 0;
  color: white;
  padding: 5%;
}

.card-image{
  width: 342px;
 
}

#SingleFilm:hover .card-image{
  width: 342px;
  cursor: pointer;
  scale: 1.2;
  z-index: 1;
}

#SingleFilm:hover .card-body{
  display: block;
  width: 342px;
 
}

</style>