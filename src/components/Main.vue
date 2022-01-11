<template>
    <main>
        <div class="container">
            <div class="card">
                <ul v-for="item, index in requestItems" :key="index">
                    <li>Titolo: {{ item.title }}</li>
                    <li>Titolo Originale: {{ item.original_title }}</li>
                    <li>Lingua: {{ item.original_language }}</li>
                    <li>Voto: {{ item.vote_average }}</li>
                </ul>
            </div>
        </div>
    </main>
</template>

<script>
export default {
    name: "Main",
    props: {
        requestItems: Array
    }
}
</script>

<style lang="scss" scoped>
main {
    // test 
    height: calc(100% - 114px);
    overflow-y: auto;
    background-color: gray;

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
            }
        }
    }
}
</style>