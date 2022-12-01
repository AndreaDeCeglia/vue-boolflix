<template>
    <div id="FilmList" class="my-5">
        <h6 class="text-white text-start ms-5">
            I NOSTRI FILM PREMIUM :
        </h6>
        <div id="FilmContainer" class="scrollbar overflow-auto d-flex p-5">
            <SingleFilmComp
            v-for="(element, index) in ArrayResultsApp"
            :key="index"
            :ObjMovie="element"
            :MoviesGenresArray="MoviesGenresArray"
            />
        </div>
        
            
        
    </div>
</template>

<script>
import SingleFilmComp from './SingleFilmComp.vue'

export default {
    name: 'FilmList',
    props: {
        ArrayResultsApp: Array,
        MoviesGenresArray: Array,
    },
    components: {
        SingleFilmComp,
    }
}
</script>

<style scoped lang="scss">

#FilmList{
    background-color: #141414;
}

.scrollbar::-webkit-scrollbar {
  background-color: #141414;
  border-radius: 20px;
  height: 10px;
}
.scrollbar::-webkit-scrollbar-thumb{
    background-color: #141414;
    border-radius: 20px;
    border: 1px solid red;
}

</style>