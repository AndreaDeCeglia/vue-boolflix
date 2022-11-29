<template>
  <div id="app">
    <HeaderComp
      @EmitSearchTextHeader="SearchMovie"
    />
    <MainComp/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'

// import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return{
      SearchTextAppFromHeaderToApp: ''
    }
  },
  mounted(){

  },
  methods:{

    SearchMovie(SearchText){
      this.SearchTextAppFromHeaderToApp = SearchText
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
