<template>
    <div class="card">
        <div class="front">
            <img v-if="details.poster_path !== null" class="cover" :src="imgPath + details.poster_path" alt="">
            <div v-else class="imgNull">
                <span>boolflix</span>
                <span class="main-title">{{details.title ? details.title : details.name}}</span>
            </div>
        </div>
        <div class="back">
            <ul>
                <li>Titolo: {{ details.title ? details.title : details.name }}</li>
                <li>Titolo Originale: {{ details.original_title ? details.original_title : details.original_name }}</li>
                <li>
                    Lingua: <img v-if="avaibleFlags.includes(details.original_language)" :src="require('../assets/' + details.original_language + '.png')" alt="">
                            <span v-else>{{ details.original_language }}</span>
                </li>
                <li>Voto: <span><i v-for="n in getIntfrom1to5(details.vote_average)" :key="n" class="fas fa-star yellow"></i></span> 
                        <span><i v-for="n in (maxStars - getIntfrom1to5(details.vote_average))" :key="n" class="far fa-star"></i></span>
                </li>
                <li v-if="details.overview">Overview: {{ details.overview }}</li>
            </ul>
        </div>
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
    width: 342px;
    height: 513px;
    flex-shrink: 0;
    margin: 0 5px 5px 0;
    border: 1px solid white;
    &:hover .front {
        display: none;
    }
    &:hover .back {
        display: block;
        
    }
    .front {
        display: block;
        height: 100%;

        img.cover {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .imgNull {
            height: 100%;
            background-color: white;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;

            .main-title {
                color: white;
                background-color: rgb(0, 0, 0, 0.8);
                border-radius: 5px;
                padding: 5px;
                text-transform: uppercase;
                font-style: oblique;
                text-align: center;
                font-size: 22px;
                align-self: bottom;
                position: absolute;
                top: 80%;
                left: 50%;
                transform:translate(-50%, -50%);
            }

            span {
                background-color: rgb(0, 0, 0);
                font-size: 40px;
                color: red;
                border-radius: 10px;
                text-transform: uppercase;
                padding: 15px;
            }
        }
    }

    .back {
        display: none;
        height: 100%;
        ul {
            padding: 20px;
            color: white;
            background-color: rgb(0, 0, 0, 0.8);
            width: 100%;
            height: 100%;
            overflow-y: auto;
            li {
                padding: 5px 0;

                img {
                    height: 20px;
                }
                .yellow {
                    color: rgb(255, 217, 1);
                }
            }
        }
    }
}
</style>