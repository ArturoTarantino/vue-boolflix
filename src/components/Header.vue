<template>
    <header>
        <div class="container">
            <div class="logo-menu">
                <div class="logo">BOOLFLIX</div>

                <div>
                    <ul class="menu">
                        <li>Home</li>
                        <li>Movies</li>
                        <li>Series</li>
                        <li>My List</li>
                    </ul>
                </div>
            </div>
            
            <div class="user-utility" >
                <div v-if="appear" class="search-bar">
                    <input v-model="searchText" type="text" placeholder="inserisci il titolo">
                    <button @click="$emit('searchClicked', searchText)">search</button>
                </div>

                <i @click="toggle" class="fas fa-search"></i>
                <span>Account</span>
                <i class="fas fa-bell"></i>           
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:"Header",
    data: function() {
        return {
            searchText: '',
            appear: false
        };
    },
    methods: {
        toggle: function () {
            this.appear = !this.appear;
        }
    }
}
</script>

<style lang="scss" scoped>
header { 
    height: 75px;
    background-color: black;
    color: white;

    .container {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        .logo-menu {
            display: flex;
            .logo {
                color: red;
                font-size: 38px;
            }
            .menu {
                display: flex;
                height: 100%;
                align-items: center;
                margin-left: 20px;

                li {
                    margin: 0 15px;
                    cursor: pointer;
                }
            }
        }
        .user-utility {
            .search-bar {
                display: inline-block;
                margin-right: 10px;
                input {
                    padding: 5px;
                    width: 250px;
                    &::placeholder {
                        font-style: oblique;
                        font-size: 15px;
                    }
                }    
                button {
                    padding: 5px;
                    margin-left: 5px;
                    text-transform: uppercase;
                    font-weight: bold;
                }
            }
            i {
                font-size: 20px;
                vertical-align: middle;
                cursor: pointer;
                margin: 0 10px;
            }   
        }
    }
}
</style>