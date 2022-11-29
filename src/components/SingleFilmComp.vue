<template>

  <div id="SingleFilm">
    <div class="card-image">
      <img 
      :src="`http://image.tmdb.org/t/p/w342/${ObjMovie.poster_path}`" 
      alt="Movie Poster"
      />
    </div>
    
    <div class="card-body d-none">
      <p class="card-title"> <b>Titolo: </b> {{ ObjMovie.title }}</p>
      <p class="card-title"> <b>Titolo Originale: </b> {{ ObjMovie.original_title }}</p>
      <p class="card-title"> <b>Voto: </b> {{ ObjMovie.vote_average }}</p>
      <p class="card-title"> <b>overview: </b> {{ ObjMovie.overview }}</p>
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
}

.card-image{
  width: 342px;
}

#SingleFilm:hover .card-image{
  display: none;
  width: 342px;
}

#SingleFilm:hover .card-body{
  display: block;
  width: 342px;
}

</style>