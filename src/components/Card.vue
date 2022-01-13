<template>
    <div class="card">
        <ul>
            <li class="cover-box"><img v-if="details.backdrop_path !== null" class="cover" :src="imgPath + details.backdrop_path" alt=""></li>
            <li>Titolo: {{ details.title ? details.title : details.name }}</li>
            <li>Titolo Originale: {{ details.original_title ? details.original_title : details.original_name }}</li>
            <li>
                Lingua: <img v-if="avaibleFlags.includes(details.original_language)" :src="require('../assets/' + details.original_language + '.png')" alt="">
                        <span v-else>{{ details.original_language }}</span>
            </li>
            <li>Voto: <span><i v-for="n in getIntfrom1to5(details.vote_average)" :key="n" class="fas fa-star yellow"></i></span> 
                    <span><i v-for="n in (maxStars - getIntfrom1to5(details.vote_average))" :key="n" class="far fa-star"></i></span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        details: Object
    },
    data: function() {
        return {
            imgPath: 'https://image.tmdb.org/t/p/w342',
            maxStars: 5,
            avaibleFlags: ['it', 'en']
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