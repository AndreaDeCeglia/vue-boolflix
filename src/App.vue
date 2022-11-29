<template>
  <div id="app">
    <HeaderComp
      @EmitSearchTextHeader="SearchMovie"
    />
    <MainComp
      :ArrayResultsApp="ArrayResults"
    />
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'

import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return{
      SearchTextFromHeaderToApp: '',
      SearchQueryUrl: '',
      ArrayResults: [],
    }
  },
  mounted(){
    
  },
  methods:{

    SearchMovie(SearchTextHeader){
      this.SearchTextFromHeaderToApp = SearchTextHeader
      console.log(`this is SearchTextAppFromHeaderToApp`, this.SearchTextAppFromHeaderToApp)

      this.SearchQueryUrl = 'https://api.themoviedb.org/3/search/movie?api_key=5b654d7920f6e01eb40a9029f815387d&language=en-US&page=1&include_adult=false&query='
        + this.SearchTextFromHeaderToApp;

      axios.get(this.SearchQueryUrl)
        .then((response) => {
        this.ArrayResults = response.data.results
      })
    }
  },
}



</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
