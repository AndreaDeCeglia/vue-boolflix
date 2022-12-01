<template>
  <div id="MainComp">
    
    <FilmList
        :ArrayResultsApp="ArrayResultsApp"
        :MoviesGernesArray="MoviesGenresArray"
    />

    <SeriesList
        :ArraySeriesApp="ArraySeriesApp"
        :SeriesGenresArray="SeriesGenresArray"
    />

  </div>
</template>

<script>
import FilmList from './FilmList.vue'
import SeriesList from './SeriesList.vue'

export default {
    name: 'MainComp',
    props: {
        ArrayResultsApp: Array,
        ArraySeriesApp: Array,
        MoviesGenresArray: Array,
        SeriesGenresArray: Array,
    },
    components: {
        FilmList,
        SeriesList
    },
}
</script>

<style scoped lang="scss">

#main-comp{
  background-color: #141414;
}

</style>
