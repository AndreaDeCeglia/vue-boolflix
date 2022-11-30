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
        <p class="card-title"> <b>Voto: </b> {{ ObjSeries.vote_average }}</p>
        <!-- <p class="card-title"> <b>overview: </b> {{ ObjMovie.overview }}</p> -->
      </div>
    </div>
  </template>
  
  <script>
    export default {
        name: 'SinglSeriesComp',
        props: {
            ObjSeries: Object
        }
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