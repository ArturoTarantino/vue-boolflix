<template>
    <main>
        <div class="container">
            <div v-if="moviesList.length > 0">
                <h2>Movies</h2>
                <div class="cards-movies">
                    <Card v-for="movie, index in moviesList" :key="index" :details="movie" />
                </div>
            </div>

            <div v-if="seriesList.length > 0">
                <h2>Series</h2>
                <div class="cards-series">
                    <Card v-for="series, index in seriesList" :key="index" :details="series" />
                </div>
            </div>
            
            <div v-if="checkLoad">
                <h2>Popular</h2>
                <div v-if="checkLoad" class="pre-load-search">
                    <Card v-for="popular, index in popularMovies" :key="index" :details="popular" />
                </div>

                <h2>Upcoming</h2>
                <div v-if="checkLoad" class="pre-load-search">
                    <Card v-for="upcoming, index in upcomingMovie" :key="index" :details="upcoming" />
                </div>
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
        moviesList: Array,
        seriesList: Array,
        popularMovies: Array,
        upcomingMovie: Array,
        checkLoad: Boolean
    }
}
</script>

<style lang="scss" scoped>
main {
    height: calc(100% - 75px);
    overflow-y: auto;
    background-color: gray;

    h2 {
        margin: 15px 0;
    }
    .cards-movies,
    .cards-series,
    .pre-load-search {
        display: flex;
        overflow-x: auto;
    }
}
</style>