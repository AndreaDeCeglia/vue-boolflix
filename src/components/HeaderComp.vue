<template>
  <header id="HeaderComp" class="d-flex justify-content-between align-items-center text-white">
    <!-- logo container -->
    <div id="LogoContainer">
      <img class="w-50" src="./../assets/netflix-logo-png-2582.png" alt="">
    </div>

    <nav>
			<span type="button">Home</span>
			<span type="button">Serie TV</span>
			<span type="button">Film</span>
			<span type="button">Nuovi e popolari</span>
			<span type="button">La mia lista</span>
			<span type="button">Sfoglia per lingua</span>
    </nav>
    <!-- searchbar -->
    <div class="input-group m-3">
      <span class="input-group-text" id="basic-addon1">@</span>
      <input 
        type="text" 
        class="form-control" 
        placeholder="search movie..." 
        aria-describedby="basic-addon1"
        v-model="SearchText"
        @keyup="$emit('EmitSearchTextHeader', SearchText)"
      >
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  props: {
  },
  data(){
    return{
      SearchText: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

#LogoContainer{
  width: 30%;
  img{
    height: 20%;
  }
}

nav{
  span{
    margin: 0 5px;
  }
}

.input-group{
  width: 20%;
}

</style>
