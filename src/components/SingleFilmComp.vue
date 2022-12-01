<template>

  <div id="SingleFilm">

    <a type="button" 
      data-bs-toggle="offcanvas" 
      data-bs-target="#staticBackdrop" 
      aria-controls="staticBackdrop"
    >
      
    {{ StarsRating() }}
    
    
    <div class="card-image">
      <img
        v-if="(ObjMovie.backdrop_path)" 
        :src="`http://image.tmdb.org/t/p/w342/${ObjMovie.backdrop_path}`" 
        alt="Movie Poster"
      />
      <img
        v-else
        class="not-found"
        src="https://bitsofco.de/content/images/2018/12/Screenshot-2018-12-16-at-21.06.29.png" 
        alt="Movie Poster"
      />
    </div>
    
    <div class="card-body">
      <p class="card-title"> <b>Titolo: </b> {{ ObjMovie.title }}</p>
      <p class="card-title"> <b>Titolo Originale: </b> {{ ObjMovie.original_title }}</p>
      <!-- vote section -->
      <span class="">Vote: </span>
        <span v-if="ObjMovie.vote_average < 5.5" class="text-danger">
          {{ ObjMovie.vote_average }}/10
        </span>
        <span
          v-if="ObjMovie.vote_average > 5.5 && ObjMovie.vote_average < 6.5"
          class="text-warning"
        >
          {{ ObjMovie.vote_average }}/10
        </span>
        <span
          v-if="ObjMovie.vote_average > 6.5 && ObjMovie.vote_average < 7.5"
          class="text-success"
        >
          {{ ObjMovie.vote_average }}/10
        </span>
        <span
          v-if="ObjMovie.vote_average > 7.5"
          class="text-success fs-5 fw-bold"
        >
          {{ ObjMovie.vote_average }}/10
        </span>

        <div class="d-inline" v-for="n in fullStars" :key="n">
          <font-awesome-icon icon="fa-solid fa-star" />
        </div>

        <div class="d-inline" v-if="halfStar == true">
          <font-awesome-icon icon="fa-regular fa-star-half-stroke" />
        </div>

        <div class="d-inline" v-for="x in emptyStars" :key="x + 'k'">
          <font-awesome-icon icon="fa-regular fa-star" />
        </div>
         <!-- vote section closure -->
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
    </a>

    
    <SingleMoviePage 
      class="offcanvas offcanvas-start" 
      data-bs-backdrop="static" 
      tabindex="-1" 
      id="staticBackdrop" 
      aria-labelledby="staticBackdropLabel" 
      :ObjMovie="ObjMovie"
      :StarsRating="StarsRating()"
    />

  </div>
</template>

<script>
  import SingleMoviePage from './SingleMoviePage.vue'

  export default {

      name: 'SingleFilmComp',
      props: {
          ObjMovie: Object,
          MoviesGenresArray: Array,
      },
      components: {
        SingleMoviePage,
      },
      data(){
        return {
          halfVote: 0,
          fullStars: 0,
          emptyStars: 0,
          halfStar: false,

          flags: ["it", "en", "fr", "de", "es", "ja", "pt"], 
          //      :class="(SingleMoviePageVisible = 'false') ? 'VisibleFalse' : 'VisibleTrue'"

        }
      },
      methods: {

        StarsRating(){
          //divido per 2 il voto medio
          this.halfVote = this.ObjMovie.vote_average / 2;
          // controllo se il voto a metà è un numero intero o no
          //se non è intero devo considerare che c'è una stella mezza piena quindi la variabile andrà su true per indicarne la presenza
          // le stelle piene saranno contate sulla base del voto a metà per difetto (perchè dopo c'è la mezza)
          // le stelle vuote sono 5 - le piene - una stella a metà
          if (this.halfVote != Math.floor(this.halfVote)) {
            this.halfStar = true;
            this.fullStars = Math.floor(this.halfVote);
            this.emptyStars = 5 - this.fullStars - 1;
          }
          // in questo caso non c'è nessuna mezza stella
          else {
            this.halfStar = false;
            this.fullStars = this.halfVote;
            this.emptyStars = 5 - this.fullStars;
          }
        },

        SingleMovieFocus(){
          this.SingleMoviePageVisible = true;
        }
      },
      
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

  .flag{
    width: 2rem;
  }
}

.card-image{
  width: 342px;
  max-height: 192px;
}

.not-found{
  width: 342px;
  max-height: 192px;
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

.VisibleFalse{
  display: none;
}

.VisibleTrue{
  display: block;
}

#staticBackdrop{
  width: 100vw;
  background-color: #141414;
  color: white;
}
</style>