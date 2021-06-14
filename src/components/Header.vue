<template>
    <header>
        <input type="text" placeholder="Cerca un film" v-model="toSearch">
        <button @click="search">Cerca</button>
    </header>
</template>

<script>
import axios from "axios"

export default {
    name: "Header",
    data: function() {
        return {
            toSearch: "",
            searchedResults: []
        }
    },
    methods: {
        search: function() {
            axios
                .get("https://api.themoviedb.org/3/search/movie", {
                // .get("https://api.themoviedb.org/3/movie/550?api_key=7a8821b77b6975ec33835d17332ec7b3")
                // .get("https://developers.themoviedb.org/3/search/movie", {
                    params: {
                        api_key: "7a8821b77b6975ec33835d17332ec7b3",
                        query: this.toSearch,
                        language: "it-IT"
                    }
                })
                .then( response => {
                    console.log(response);
                    this.searchedResults = response.data.results;
                    console.log(this.searchedResults);

                    this.$emit("movieFound", this.searchedResults)
                })
        }
    }
}
</script>

<style>

</style>