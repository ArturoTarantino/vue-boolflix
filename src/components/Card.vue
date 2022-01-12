<template>
    <div class="card">
        <!-- <ul v-for="item, index in requestItems" :key="index">
            <li>Titolo: {{ item.title }}</li>
            <li>Titolo Originale: {{ item.original_title }}</li>
            <li>
                Lingua: <img v-if="item.original_language === 'en' || item.original_language === 'it'" :src="require('../assets/' + item.original_language + '.png')" alt="">
                        <span v-else>{{ item.original_language }}</span>
            </li>
            <li>Voto: {{ item.vote_average }}</li>
        </ul>

        <ul v-for="item, index in seriesRequest" :key="index">
            <li>Titolo: {{ item.name }}</li>
            <li>Titolo Originale: {{ item.original_name }}</li>
            <li>
                Lingua: <img v-if="item.original_language === 'en' || item.original_language === 'it'" :src="require('../assets/' + item.original_language + '.png')" alt="">
                        <span v-else>{{ item.original_language }}</span>
            </li>
            <li>Voto: {{ item.vote_average }}</li>
        </ul> -->
        <ul v-if="movie">
            <li class="cover-box"><img v-if="movie.backdrop_path !== null" class="cover" :src="imgPath + movie.backdrop_path" alt=""></li>
            <li>Titolo: {{ movie.title }}</li>
            <li>Titolo Originale: {{ movie.original_title }}</li>
            <li>
                Lingua: <img v-if="movie.original_language === 'en' || movie.original_language === 'it'" :src="require('../assets/' + movie.original_language + '.png')" alt="">
                        <span v-else>{{ movie.original_language }}</span>
            </li>
            <li>Voto: <span><i v-for="n in getIntfrom1to5(movie.vote_average)" :key="n" class="fas fa-star yellow"></i></span> 
                    <span><i v-for="n in (maxStars - getIntfrom1to5(movie.vote_average))" :key="n" class="far fa-star"></i></span>
            </li>
        </ul>
        <ul v-else-if="series">
            <li class="cover-box"><img v-if="series.backdrop_path !== null" class="cover" :src="imgPath + series.backdrop_path" alt=""></li>
            <li>Titolo: {{ series.name }}</li>
            <li>Titolo Originale: {{ series.original_name }}</li>
            <li>
                Lingua: <img v-if="series.original_language === 'en' || series.original_language === 'it'" :src="require('../assets/' + series.original_language + '.png')" alt="">
                        <span v-else>{{ series.original_language }}</span>
            </li>
            <li>Voto: <span><i v-for="n in getIntfrom1to5(series.vote_average)" :key="n" class="fas fa-star yellow"></i></span>
                    <span><i v-for="n in (maxStars - getIntfrom1to5(series.vote_average))" :key="n" class="far fa-star"></i></span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        // requestItems: Array,
        // seriesRequest: Array
        movie: Object,
        series: Object
    },
    data: function() {
        return {
            imgPath: 'https://image.tmdb.org/t/p/w342',
            maxStars: 5,
        }
    },
    methods: {
        getIntfrom1to5: function(number) {
            return Math.round(number / 2);
        }
    }
}
</script>

<style lang="scss" scoped>
.card {
    // display: flex;
    // flex-wrap: wrap;
    width: calc(100% / 3 - 10px);
    min-height: 300px;
    // padding-top: 50px;
    margin: 5px 10px 5px 0;
    ul {
        background-color: white;
        width: 100%;
        height: 100%;
        li {
            padding: 5px 0;

            img {
                height: 20px;
            }
            .yellow {
                color: rgb(255, 217, 1);
            }
        }
        .cover-box {
            text-align: center;
            min-height: 183px;
            .cover {
            height: 170px;
        }
        }
    }
}
</style>