<template>
    <header>
        <a href="#">
            <img src="../assets/images/logo.png" alt="">
        </a>
        <div class="searchbar">
            <input type="text" placeholder="Cerca un film" v-model="toSearch" @keyup.enter="search">
        </div>
    </header>
</template>

<script>
import axios from "axios"

export default {
    name: "Header",
    data: function() {
        return {
            toSearch: "",
            allResults: [],
            movies: [],
            series: [],
        }
    },
    methods: {
        search: function() {
            const paramsObj = {
                    params: {
                        api_key: "7a8821b77b6975ec33835d17332ec7b3",
                        query: this.toSearch,
                        language: "it-IT"
                    }
                };

            axios
                .get("https://api.themoviedb.org/3/search/movie", paramsObj)
                .then( response => {
                    console.log(response);
                    this.movies = response.data.results;

                    this.$emit("moviesFound", this.movies)
                })
                
            axios
                .get("https://api.themoviedb.org/3/search/tv", paramsObj)
                .then( response => {
                    console.log(response);
                    this.series = response.data.results;

                    this.$emit("seriesFound", this.series)
                })
        }
    }
}
</script>

<style lang="scss" scoped>
    header {
        height: 100px;
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        position: fixed;
        top: 0;
        z-index: 1;

        a {
            margin-left: 20px;
        }

        .searchbar {
            margin-right: 20px;

            input {
                font-size: 18px;
                width: 300px;
                padding: 5px;
            }
        }
    }
</style>