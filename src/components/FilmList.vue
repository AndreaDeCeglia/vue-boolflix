<template>
    <div id="FilmList">
        <h3 class="text-white text-start ms-5">
            I NOSTRI FILM PREMIUM :
        </h3>
        <div id="FilmContainer" class="overflow-auto d-flex p-5">
            <SingleFilmComp
            v-for="(element, index) in ArrayResultsApp"
            :key="index"
            :ObjMovie="element"
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

</style>