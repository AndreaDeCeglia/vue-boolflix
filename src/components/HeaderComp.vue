<template>
  <header id="HeaderComp" class="container d-flex justify-content-between align-items-center p-5 bg-dark text-white">
    <!-- logo container -->
    <div id="LogoContainer">
      LOGO
    </div>
    <!-- searchbar -->
    <div class="input-group mb-3 w-50">
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

</style>
