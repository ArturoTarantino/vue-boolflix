<template>
    <main>
        <div class="container">
            <div class="movies">
                <h2>Movies</h2>
                <Card :requestItems="requestItems" />
            </div>
            <div class="series">
                <h2>Series</h2>
                <Card :seriesRequest="seriesRequest" />
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
        seriesRequest: Array
    }
}
</script>

<style lang="scss" scoped>
main {
    // test 
    height: calc(100% - 75px);
    overflow-y: auto;
    background-color: gray;
}
</style>