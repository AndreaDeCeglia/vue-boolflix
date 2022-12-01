<template>
  <div id="SingleMoviePage" class="text-white">
    
    <!-- {{ StarsRating() }} -->
    
    <div class="offcanvas-header">
      <div id="LogoContainer">
        <img class="w-50" src="./../assets/netflix-logo-png-2582.png" alt="">
      </div>
      <button type="button" class="btn-close bg-danger" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    
    <div class="offcanvas-body d-flex ms-5">
      <div>
        <img 
          :src="`http://image.tmdb.org/t/p/w342/${ObjMovie.poster_path}`" 
          alt="Movie Poster"
        />
      </div>
      
      <div id="info">
        <p class="card-title"> <b>Titolo: </b> {{ ObjMovie.title }}</p>
        <p class="card-title"> <b>Titolo Originale: </b> {{ ObjMovie.original_title }}</p>
         <!-- language section -->
         <img
          v-if="flags.includes(ObjMovie.original_language)"
          :src="require(`../assets/${ObjMovie.original_language}.svg`)"
          class="flag"
          />
          <p v-else>
            Lingua Originale: {{ ObjMovie.original_language.toUpperCase() }}
          </p>
        <!-- Language section closure -->
      </div>

    </div>
  </div>
</template>

<script>
export default {
    name: 'SingleMoviePage',
    props: {
        ObjMovie: Object,
        StarsRating: Function,
    },
    data(){
        return {
          halfVote: 0,
          fullStars: 0,
          emptyStars: 0,
          halfStar: false,

          flags: ["it", "en", "fr", "de", "es", "ja", "pt"],
        }
    },
    
}
</script>

<style scoped lang="scss">

.flag{
    width: 2rem;
  }

</style>