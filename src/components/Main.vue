<template>
    <main>
        <div class="container">
            <h2 v-if="checkLoad">Movies</h2>
            <div class="cards-movies">
                <Card v-for="item, index in requestItems" :key="index" :movie="item" />
            </div>
            <h2 v-if="checkLoad">Series</h2>
            <div class="cards-series">
                <Card v-for="item, index in seriesRequest" :key="index" :series="item" />
            </div>
        </div>
    </main>
</template>

<script>
import Card from './Card.vue';

export default {
    name: "Main",
    components: {
        Card
    },
    props: {
        requestItems: Array,
        seriesRequest: Array,
        checkLoad: Boolean
    }
}
</script>

<style lang="scss" scoped>
main {
    // test 
    height: calc(100% - 75px);
    overflow-y: auto;
    background-color: gray;

    h2 {
        margin: 15px 0;
    }
    .cards-movies,
    .cards-series {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>