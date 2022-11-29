<template>
  <div id="MainComp">

    <FilmList
        :ArrayResultsApp="ArrayResultsApp"
    />

  </div>
</template>

<script>
import FilmList from './FilmList.vue'

export default {
    name: 'MainComp',
    props: {
        ArrayResultsApp: Array,
    },
    components: {
        FilmList,
    },
}
</script>

<style>

</style>
