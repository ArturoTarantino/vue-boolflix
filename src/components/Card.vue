<template>
    <div class="card">
        <ul v-for="item, index in requestItems" :key="index">
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
        </ul>
    </div>
</template>

<script>
export default {
    name: "MovieCard",
    props: {
        requestItems: Array,
        seriesRequest: Array
    }
}
</script>

<style lang="scss" scoped>
.card {
    display: flex;
    flex-wrap: wrap;
    padding-top: 50px;
    ul {
        background-color: white;
        width: calc(100% / 3 - 10px);
        margin: 5px;
        li {
            padding: 5px 0;

            img {
                height: 20px;
            }
        }
    }
}
</style>