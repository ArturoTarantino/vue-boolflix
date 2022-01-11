<template>
    <header>
        <div class="container">
            <div class="logo">
                BOOLFLIX
            </div>
            <div class="search-bar">
                <input v-model="searchText" type="text" placeholder="inserisci il titolo">
                <button @click="$emit('searchClicked', searchText)">search</button>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:"Header",
    data: function() {
        return {
            searchText: ''
        };
    },
    methods: {
        
    }
}
</script>

<style lang="scss" scoped>
header {
    // test 
    height: 75px;
    background-color: black;

    .container {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;

        .logo {
            color: red;
            font-size: 28px;
        }
        
        .search-bar {
            input {
                padding: 5px;
                width: 250px;
            }
            button {
                padding: 5px;
                margin-left: 5px;
                text-transform: uppercase;
                font-weight: bold;
            }
        }
    }
}
</style>