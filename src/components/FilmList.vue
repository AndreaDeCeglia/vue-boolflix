<template>
    <div id="FilmList" class="overflow-auto d-flex">
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

<style scoped lang="scss">



</style>