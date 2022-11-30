<template>

    <div id="SingleSeries">
      <div class="card-image">
        <img 
        :src="`http://image.tmdb.org/t/p/w342/${ObjSeries.backdrop_path}`" 
        alt="Series Poster"
        />
      </div>
      
      <div class="card-body">
        <p class="card-title"> <b>Titolo: </b> {{ ObjSeries.name }}</p>
        <p class="card-title"> <b>Titolo Originale: </b> {{ ObjSeries.original_title }}</p>
        <span class="">Vote: </span>
        <span v-if="ObjSeries.vote_average < 5.5" class="text-danger">
          {{ ObjSeries.vote_average }}/10
        </span>
        <span
          v-if="ObjSeries.vote_average > 5.5 && ObjSeries.vote_average < 6.5"
          class="text-warning"
        >
          {{ ObjSeries.vote_average }}/10
        </span>
        <span
          v-if="ObjSeries.vote_average > 6.5 && ObjSeries.vote_average < 7.5"
          class="text-success"
        >
          {{ ObjSeries.vote_average }}/10
        </span>
        <span
          v-if="ObjSeries.vote_average > 7.5"
          class="text-success fs-5 fw-bold"
        >
          {{ ObjSeries.vote_average }}/10
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
         <!-- language section -->
        <img
          v-if="flags.includes(ObjSeries.original_language)"
          :src="require(`../assets/${ObjSeries.original_language}.svg`)"
          class="flag"
        />
        <p v-else>
          Lingua Originale: {{ ObjSeries.original_language.toUpperCase() }}
        </p>
        <!-- Language section closure -->
      </div>
    </div>
  </template>
  
  <script>
    export default {
        name: 'SinglSeriesComp',
        props: {
            ObjSeries: Object
        },
        data(){
            return{
                halfVote: 0,
                fullStars: 0,
                emptyStars: 0,
                halfStar: false,

                flags: ["it", "en", "fr", "de", "es", "ja", "pt"],
            }
        },
        methods: {

            StarsRating(){
            //divido per 2 il voto medio
            this.halfVote = this.ObjSeries.vote_average / 2;
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
                this.fullStars = this.halfVote;
                this.emptyStars = 5 - this.fullStars;
            }
            },
            
        },
        mounted(){
                this.StarsRating();
        },
    }
  </script>
  
  <style scoped lang="scss">
  
  #SingleSeries{
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
   
  }
  
  #SingleSeries:hover .card-image{
    width: 342px;
    cursor: pointer;
    scale: 1.2;
    z-index: 1;
  }
  
  #SingleSeries:hover .card-body{
    display: block;
    width: 342px;
   
  }
  
  </style>