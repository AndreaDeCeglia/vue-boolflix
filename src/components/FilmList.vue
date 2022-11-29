<template>
    <div id="FilmList" class="d-flex justify-content-between align-items-center flex-wrap">
        <SingleFilmComp
        v-for="(element, index) in ArrayResultsApp"
        :key="index"
        :ObjMovie="element"
        />
            
        
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

<style>

</style>