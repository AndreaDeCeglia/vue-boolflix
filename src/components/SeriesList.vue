<template>
    <div id="SeriesList" class="my-5">
        <h6 class="text-white text-start ms-5">
            LE NOSTRE SERIE PREMIUM :
        </h6>
        <div id="SeriesContainer" class="scrollbar overflow-auto d-flex p-5">
            <SingleSeriesComp
            v-for="(element, index) in ArraySeriesApp"
            :key="index"
            :ObjSeries="element"
            />
        </div>
        
            
        
    </div>
</template>

<script>
import SingleSeriesComp from './SingleSeriesComp.vue'

export default {
    name: 'SeriesList',
    props: {
        ArraySeriesApp: Array,
        SeriesGenresArray: Array,
    },
    components: {
        SingleSeriesComp,
    }
}
</script>

<style scoped lang="scss">

#SeriesList{
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